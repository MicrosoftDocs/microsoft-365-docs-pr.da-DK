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
description: Sammenlign Microsoft 365, herunder ome Office 365-meddelelseskryptering (OME), S/MIME,IRM (Information Rights Management), og få mere at vide om Transport Layer Security (TLS).
ms.openlocfilehash: 1d6ad4f595652b39ff6e984afe096272a7920c4d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587905"
---
# <a name="email-encryption"></a>Mailkryptering

I denne artikel sammenlignes krypteringsindstillingerne i Microsoft 365 herunder Office 365-meddelelseskryptering (OME), S/MIME, IRM (Information Rights Management) og introducerer TLS (Transport Layer Security).
  
Microsoft 365 leverer flere krypteringsmuligheder, som kan hjælpe dig med at opfylde virksomhedens behov for mailsikkerhed. I denne artikel beskrives tre måder at kryptere mail på Office 365. Hvis du vil vide mere om alle sikkerhedsfunktioner i Office 365, kan du besøge [Office 365 Center for sikkerhed og sikkerhed](https://go.microsoft.com/fwlink/p/?LinkID=282470). I denne artikel introduceres de tre typer kryptering, der er tilgængelige for Microsoft 365, som hjælper med at sikre mail i Office 365:
  
- Office ome (Message Encryption).

- Secure/Multipurpose Internet Mail Extensions (S/MIME).

- IRM (Information Rights Management).

## <a name="how-microsoft-365-uses-email-encryption"></a>Sådan Microsoft 365 mailkryptering

Kryptering er den proces, som oplysninger kodes efter, så kun en autoriseret modtager kan afkode og bruge oplysningerne. Microsoft 365 bruger kryptering på to måder: i tjenesten og som kundekontrol. I tjenesten bruges kryptering som Microsoft 365, men du behøver ikke at konfigurere noget. Eksempelvis bruger Microsoft 365 TLS (Transport Layer Security) til at kryptere forbindelsen eller sessionen mellem to servere. 
  
Sådan fungerer mailkryptering typisk:
  
- En meddelelse krypteres eller omdannes fra almindelig tekst til ulæselig kode, enten på afsenderens computer eller på en central server, mens meddelelsen er under overførsel.

- Meddelelsen forbliver i ciphertext, mens den er under overførsel, for at beskytte den mod at blive læst, hvis meddelelsen opsnappes.

- Når meddelelsen modtages af modtageren, omdannes meddelelsen tilbage til læsbar almindelig tekst på en af to måder:

  - Modtagerens computer bruger en nøgle til at dekryptere meddelelsen, eller

  - En central server dekrypterer meddelelsen på vegne af modtageren, efter validering af modtagerens identitet.

Du kan finde flere oplysninger om, hvordan Microsoft 365 sikrer kommunikationen mellem servere, f.eks. mellem organisationer inden for Microsoft 365 eller mellem Microsoft 365 og en pålidelig forretningspartner uden for Microsoft 365 i [Exchange Online  bruger TLS til at sikre mailforbindelser i Office 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Sammenligning af de mailkrypteringsindstillinger, der er tilgængelige i Office 365

|Teknologi til mailkryptering|![Begrebsmæssig illustration, der beskriver OME.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![Begrebsmæssig illustration, der beskriver IRM](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![Konceptuel illustration, der beskriver SMIME](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Hvad er det?|Office 365-meddelelseskryptering (OME) er en tjeneste, der er bygget på Azure Rights Management (Azure RMS), som gør det muligt at sende krypterede mails til personer i eller uden for organisationen uanset destinationsmailadressen (Gmail, Yahoo! Mail, Outlook.com osv.). <br/> Som administrator kan du konfigurere transportregler, der definerer betingelserne for kryptering. Når en bruger sender en meddelelse, der svarer til en regel, anvendes krypteringen automatisk. <br/> Hvis du vil have vist krypterede meddelelser, kan modtagerne enten få en engangs adgangskode, logge på med en Microsoft-konto eller logge på med en arbejds- eller skolekonto, der er knyttet til Office 365. Modtagerne kan også sende krypterede svar. De behøver ikke et abonnement på Microsoft 365 for at få vist krypterede meddelelser eller sende krypterede svar.|IRM er en krypteringsløsning, der også anvender brugsbegrænsninger på mails. Det er med til at forhindre følsomme oplysninger i at blive udskrevet, videresendt eller kopieret af uautoriserede personer. <br/> IRM-funktioner i Microsoft 365 i Azure Rights Management (Azure RMS).|S/MIME er en certifikatbaseret krypteringsløsning, der gør det muligt både at kryptere og signere en meddelelse digitalt. Meddelelseskryptering er med til at sikre, at det kun er den tilsigtede modtager, der kan åbne og læse meddelelsen. En digital signatur hjælper modtageren med at validere afsenderens identitet. <br/> Både digitale signaturer og meddelelseskryptering er gjort mulige ved hjælp af unikke digitale certifikater, der indeholder nøgler til bekræftelse af digitale signaturer og kryptering eller dekryptering af meddelelser. <br/> Hvis du vil bruge S/MIME, skal der være offentlige nøgler på filen for hver modtager. Modtagerne skal opbevare deres egne private nøgler, som skal forblive sikre. Hvis en modtagers private nøgler kompromitteres, skal modtageren have en ny privat nøgle og omfordele offentlige nøgler til alle potentielle afsendere.|
|Hvad gør den?|OME: <br/> Krypterer meddelelser, der sendes til interne eller eksterne modtagere. <br/>  Giver brugerne mulighed for at sende krypterede meddelelser til alle mailadresser, Outlook.com, Yahoo! Mail og Gmail. <br/>  Gør det muligt som administrator at tilpasse mailvisningsportalen, så den afspejler organisationens brand. <br/> Microsoft administrerer og gemmer nøgler sikkert, så det behøver du ikke selv. <br/> Der kræves ingen særlig software på klientsiden, så længe den krypterede meddelelse (sendt som en vedhæftet HTML-fil) kan åbnes i en browser.|IRM: <br/> Bruger krypterings- og brugsbegrænsninger til at give online- og offlinebeskyttelse af mails og vedhæftede filer. <br/> Giver dig som administrator mulighed for at konfigurere transportregler eller Outlook til automatisk at anvende IRM til at vælge meddelelser. <br/> Giver brugerne mulighed for manuelt at anvende skabeloner i Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App).|S/MIME adresserer godkendelse af afsender med digitale signaturer og meddelelsens fortrolighed med kryptering.|
|Hvad gør den ikke?|OME lader dig ikke anvende brugsbegrænsninger på meddelelser. Du kan f.eks. ikke bruge den til at forhindre en modtager i at videresende eller udskrive en krypteret meddelelse.|Nogle programmer understøtter muligvis ikke IRM-mails på alle enheder. Du kan finde flere oplysninger om disse og andre produkter, der understøtter IRM-mail, under [Egenskaber for klientenhed](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME tillader ikke, at krypterede meddelelser scannes for malware, spam eller politikker.|
|Anbefalinger og eksempelscenarier|Vi anbefaler, at du bruger OME, når du vil sende følsomme forretningsoplysninger til personer uden for organisationen, uanset om det er forbrugere eller andre virksomheder. Eksempel:  <br/>  En bankmedarbejder sender kreditkortopgørelser til kunder  <br/>  En læge sender lægejournaler til en patient  <br/>  En advokat sender fortrolige juridiske oplysninger til en anden advokat|Vi anbefaler, at du bruger IRM, når du vil anvende brugsbegrænsninger samt kryptering. Eksempel:  <br/>  En chef, der sender fortrolige oplysninger til sit team om et nyt produkt, anvender indstillingen "Videresende ikke".  <br/>  En leder skal dele et tilbud med en anden virksomhed, hvilket omfatter en vedhæftet fil fra en partner, der bruger Office 365, og kræve, at både mailen og den vedhæftede fil skal være beskyttet.|Vi anbefaler, at du bruger S/MIME, når enten din organisation eller modtagerens organisation kræver peer-to-peer-kryptering.  <br/>  S/MIME bruges oftest i følgende scenarier:  <br/>  Offentlige myndigheder, der kommunikerer med andre offentlige myndigheder  <br/>  En virksomhed, der kommunikerer med et offentligt organ|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Hvilke krypteringsindstillinger er tilgængelige for mit Microsoft 365 abonnement?

Du kan finde oplysninger om indstillinger for mailkryptering Microsoft 365 dit abonnement i [Exchange Online tjenestebeskrivelsen](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Her kan du finde oplysninger om følgende krypteringsfunktioner:
  
- Azure RMS, herunder både IRM-funktioner og OME

- S/MIME

- TLS

- Kryptering af in restdata (via BitLocker)

Du kan også bruge krypteringsværktøjer fra tredjepart med Microsoft 365 f.eks. PGP (Pretty Good Privacy). Microsoft 365 understøtter ikke PGP/MIME, og du kan kun bruge PGP/Inline til at sende og modtage PGP-krypterede mails.

## <a name="what-about-encryption-for-data-at-rest"></a>Hvad med kryptering af in rest-data?

"In rest-data" henviser til data, der ikke er aktivt under overførsel. In Microsoft 365, email data at rest er krypteret ved hjælp BitLocker drive encryption. BitLocker krypterer harddiske i Microsofts datacentre for at give forbedret beskyttelse mod uautoriseret adgang. Du kan få mere at vide [under Oversigt over BitLocker](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>Flere oplysninger om indstillinger for mailkryptering

Du kan finde flere oplysninger om indstillinger for mailkryptering i denne artikel samt TLS i følgende artikler:
  
**OME**
  
[Office 365-meddelelseskryptering (OME)](ome.md)
  
**IRM**
  
[Information Rights Management i Exchange Online](./information-rights-management-in-exchange-online.md)
  
[Hvad er Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[S/MIME til signering og kryptering af meddelelser](/Exchange/policy-and-compliance/smime/smime)
  
[Forstå S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Forstå offentlig nøglekryptografi](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Konfigurere brugerdefineret mailflow ved hjælp af forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
