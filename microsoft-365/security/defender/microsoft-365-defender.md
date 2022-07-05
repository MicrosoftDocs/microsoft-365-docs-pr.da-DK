---
title: Hvad er Microsoft 365 Defender?
description: Microsoft 365 Defender er en koordineret trusselsbeskyttelsesløsning, der er udviklet til at beskytte enheder, identitet, data og programmer
keywords: introduktion til MMicrosoft 365 Defender, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- admindeeplinkDEFENDER
- intro-overview
ms.topic: conceptual
ms.technology: m365d
adobe-target: true
ms.openlocfilehash: de40589c69aee6c6ab959f360b384707eca3d29a
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617124"
---
# <a name="what-is-microsoft-365-defender"></a>Hvad er Microsoft 365 Defender?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender er en samlet virksomhedsforsvarspakke før og efter sikkerhedsbrud, der oprindeligt koordinerer registrering, forebyggelse, undersøgelse og svar på tværs af slutpunkter, identiteter, mail og programmer for at yde integreret beskyttelse mod avancerede angreb.

Med den integrerede Microsoft 365 Defender løsning kan sikkerhedseksperter samle de trusselssignaler, som hvert af disse produkter modtager, og bestemme det fulde omfang og den fulde indvirkning af truslen, hvordan den gik ind i miljøet, hvad det påvirkes, og hvordan det i øjeblikket påvirker organisationen. Microsoft 365 Defender udfører automatisk handlinger for at forhindre eller stoppe angreb og selvreparerende berørte postkasser, slutpunkter og brugeridentiteter.

<center><h2>Microsoft 365 Defender-tjenester</center></h2>
<table><tr><td><center><b><a href="/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint"><b>Microsoft Defender for Endpoint</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management"><b>Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/office-365-security/overview"><b>Microsoft Defender for Office 365</b></center></a></td>
<td><center><b><a href="/defender-for-identity/"><b>Microsoft Defender for Identity</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Defender for Cloud Apps</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Microsoft 365 Defender interaktiv vejledning

I denne interaktive vejledning lærer du, hvordan du beskytter din organisation med Microsoft 365 Defender. Du kan se, hvordan Microsoft 365 Defender kan hjælpe dig med at registrere sikkerhedsrisici, undersøge angreb på din organisation og forhindre skadelige aktiviteter automatisk.

[Se den interaktive vejledning](https://aka.ms/M365Defender-InteractiveGuide)

## <a name="microsoft-365-defender-protection"></a>Microsoft 365 Defender beskyttelse

Microsoft 365 Defender tjenester beskytter:

- **Slutpunkter med Defender for Endpoint** – Defender for Endpoint er en samlet slutpunktsplatform til forebyggende beskyttelse, registrering efter brud, automatiseret undersøgelse og svar.
- **Assets with Defender Vulnerability Management** – Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender leverer løbende synlighed af aktiver, intelligente risikobaserede vurderinger og indbyggede afhjælpningsværktøjer, der kan hjælpe dine sikkerheds- og it-teams med at prioritere og håndtere kritiske sikkerhedsrisici og fejlkonfigurationer på tværs af din Organisation.
- **Mail og samarbejde med Defender for Office 365** – Defender for Office 365 beskytter din organisation mod skadelige trusler fra mailmeddelelser, links (URL-adresser) og samarbejdsværktøjer.
- **Identiteter med Defender for Identity og Azure Active Directory (Azure AD) Identity Protection** – Defender for Identity bruger dine AD DS-signaler (Active Directory i det lokale miljø Domain Services) til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation. Azure AD Identity Protection automatiserer registrering og afhjælpning af identitetsbaserede risici i dine cloudbaserede Azure AD.
- **Programmer med Microsoft Defender for Cloud Apps** – Microsoft Defender for Cloud Apps er en omfattende saaS-løsning, der giver dig dyb synlighed, stærke datakontroller og forbedret trusselsbeskyttelse af dine cloudapps.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww]

Microsoft 365 Defender unikke lag på tværs af produkter øger de enkelte tjenestekomponenter til:

- Hjælp med at beskytte mod angreb og koordinere defensive svar på tværs af tjenesterne via signaldeling og automatiserede handlinger.
- Indtal hele historien om angrebet på tværs af produktbeskeder, funktionsmåder og kontekst for sikkerhedsteams ved at sammenføje data i beskeder, mistænkelige hændelser og påvirkede aktiver til 'hændelser'.
- Automatiser reaktion på kompromis ved at udløse selvreparation for påvirkede aktiver gennem automatiseret afhjælpning.
- Gør det muligt for sikkerhedsteams at udføre detaljeret og effektiv trusselsjagt på tværs af slutpunkts- og Office-data.

Her er et eksempel på, hvordan Microsoft 365 Defender-portalen korrelerer alle relaterede beskeder på tværs af produkter til en enkelt hændelse.

:::image type="content" source="../../media/overview-incident.png" alt-text="Siden oversigt over hændelser" lightbox="../../media/overview-incident.png":::

Her er et eksempel på listen over relaterede beskeder for en hændelse.

:::image type="content" source="../../media/incident-list.png" alt-text="Listen over beskeder om en hændelse" lightbox="../../media/incident-list.png":::

Her er et eksempel på forespørgselsbaseret jagt oven på rådata om mail og slutpunkter.

:::image type="content" source="../../media/advanced-hunting.png" alt-text=" Siden Avanceret jagt med forespørgselsoplysninger" lightbox="../../media/advanced-hunting.png":::

Microsoft 365 Defender funktioner på tværs af produkter omfatter:

- **Enkelt glasrude på tværs af produkter på Microsoft 365 Defender-portalen** – en central visning af alle oplysninger om registreringer, påvirkede aktiver, automatiserede handlinger og relaterede beviser i en enkelt kø og en enkelt rude i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal.</a> 
- **Kombineret hændelseskø** – For at hjælpe sikkerhedseksperter med at fokusere på det, der er vigtigt, ved at sikre, at det fulde angrebsomfang, påvirkede aktiver og automatiserede afhjælpningshandlinger grupperes og vises rettidigt. 
- **Automatisk reaktion på trusler** – Vigtige trusselsoplysninger deles i realtid mellem de Microsoft 365 Defender produkter for at hjælpe med at stoppe et angrebs forløb. 

   Hvis der f.eks. registreres en skadelig fil på et slutpunkt, der er beskyttet af Defender for Endpoint, instrueres Defender for Office 365 i at scanne og fjerne filen fra alle mails. Filen blokeres, når hele Microsoft 365-sikkerhedspakken vises.

- **Selvreparerende for kompromitterede enheder, brugeridentiteter og postkasser** – Microsoft 365 Defender bruger AI-drevne automatiske handlinger og playbooks til at afhjælpe påvirkede aktiver tilbage til en sikker tilstand. Microsoft 365 Defender udnytter automatisk afhjælpningsmuligheder for pakkeprodukterne for at sikre, at alle påvirkede aktiver, der er relateret til en hændelse, afhjælpes automatisk, hvor det er muligt.
- **Jagt på tværs af produkter** – Sikkerhedsteams kan udnytte deres unikke organisationsviden til at jage efter tegn på kompromis ved at oprette deres egne brugerdefinerede forespørgsler om de rå data, der indsamles af de forskellige beskyttelsesprodukter. Microsoft 365 Defender giver forespørgselsbaseret adgang til 30 dages historiske rådata og beskeddata på tværs af slutpunkts- og Defender for Office 365 data.

## <a name="get-started"></a>Kom i gang

Microsoft 365 Defender licenskrav skal være opfyldt, før du kan aktivere tjenesten på Microsoft 365 Defender-portalen på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> Du kan få flere oplysninger under:

- [Licenskrav](prerequisites.md#licensing-requirements)
- [Slå Microsoft 365 Defender til](m365d-enable.md)
