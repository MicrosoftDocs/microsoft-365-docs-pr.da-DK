---
title: Microsoft 365 Security for Business Decision Makers (BDMs)
description: De mest almindelige scenarier med trusler og angreb, som organisationer i øjeblikket står over for Microsoft 365 deres sikkerhedsmiljøer, og anbefalede handlinger til at mindske disse risici.
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: johmar
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.openlocfilehash: 67943bc533c55961a2ceabbe89a0fe41c231ff71
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473183"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 Security for Business Decision Makers (BDMs)

I denne artikel beskrives nogle af de mest almindelige scenarier med trusler og angreb, som organisationer i øjeblikket står over for for deres Microsoft 365-miljøer, og anbefalede handlinger til at mindske disse risici. Selvom Microsoft 365 leveres med en lang række forudkonfigurerede sikkerhedsfunktioner, kræver det også, at du som kunde tager ansvaret for at sikre dine egne identiteter, data og enheder, der bruges til at få adgang til skytjenester. Denne vejledning er udviklet af Kozeta Beam (Microsoft Cloud Security Architect) og Taragaraj Sundararaplatform (Microsoft Senior Consultant).

Denne artikel er organiseret efter prioritet af arbejde, startende med at beskytte disse konti, der bruges til at administrere de mest kritiske tjenester og aktiver, f.eks din lejer, mail og SharePoint. Det er en metodisk metode til at nærmer sikkerhed og arbejder sammen med følgende regneark, så du kan spore fremskridt med interessenter og teams i hele organisationen: [Microsoft 365 sikkerhed for regneark med BDMs](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Et eksempel på Microsoft 365 BDM security recommendation spreadhsheet" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Microsoft giver dig Secure Score-værktøjet i din lejer, så du automatisk kan analysere din sikkerhedsstilling ud fra dine almindelige aktiviteter, tildele et resultat og komme med anbefalinger til forbedring af sikkerheden. Før du tager de anbefalede handlinger i denne artikel, skal du notere dig dine aktuelle resultater og anbefalinger. De handlinger, der anbefales i denne artikel, øger din score. Målet er ikke at opnå det højeste antal point, men at være opmærksom på mulighederne for at beskytte dit miljø på en måde, der ikke påvirker produktiviteten for dine brugere negativt. Se [Microsoft Secure Score](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Trinene til at reducere risici for din virksomhed" lightbox="../media/security/security-for-bdms-overview.png":::

En ting mere, før vi går i gang. . . Sørg for at [aktivere overvågningsloggen](../compliance/search-the-audit-log-in-security-and-compliance.md). Du skal bruge disse data senere, i tilfælde af at du har brug for at undersøge en hændelse eller et brud.

## <a name="protect-privileged-accounts"></a>Beskyt konti med rettigheder

Som det første trin anbefaler vi at sikre, at kritiske konti i miljøet får et ekstra lag beskyttelse, da disse konti har adgang og tilladelser til at administrere og ændre kritiske tjenester og ressourcer, hvilket kan påvirke hele organisationen negativt, hvis de kompromitteres. Beskyttelse af privilegerede konti er en af de mest effektive måder at beskytte sig mod en hacker, der forsøger at øge tilladelserne for en kompromitteret konto til en administrativ person.

|Anbefaling  |E3 |E5  |
|---------|---------|---------|
|Gennemtving multifaktorgodkendelse (MFA) for alle administrative konti.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|Implementer Azure Active Directory (Azure AD) Privileged Identity Management (PIM) for at anvende just-in-time-privilegeret adgang til Azure AD og Azure-ressourcer. Du kan også finde ud af, hvem der har adgang til og gennemgår adgangspriviligerede rettigheder.|         | ![grønt afkrydsning.](../media/green-check-mark.png)|
|Implementer adgangsstyring med rettigheder til at administrere detaljeret adgangskontrol over privilegerede administratoropgaver Office 365. |         | ![grønt afkrydsning.](../media/green-check-mark.png)|
|Konfigurer og brug privileged access workstations (AFSER) til at administrere tjenester. Brug ikke de samme arbejdsstationer til at søge på internettet og tjekke mails, der ikke er relateret til din administrative konto.|  !![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)::: |

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="De anbefalede funktioner til beskyttelse af privilegerede konti" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Yderligere anbefalinger:

- Sørg for, at konti, der synkroniseres fra det lokale miljø, ikke tildeles administratorroller til skytjenester. Dette hjælper med at forhindre en hacker i at anvende lokale konti for at få administrativ adgang til skytjenester.
- Sørg for, at tjenestekonti ikke tildeles administratorroller. Disse konti overvåges ofte ikke og angives med adgangskoder, der ikke udløber. Start med at sikre, at kontiene AADConnect og ADFS ikke er globale administratorer som standard.
- Fjern licenser fra administratorkonti. Medmindre der er en bestemt use case til at tildele licenser til bestemte administratorkonti, skal du fjerne licenser fra disse konti.

## <a name="reduce-the-surface-of-attack"></a>Reducer angrebsoverfladen

Det næste fokusområde er at reducere angrebsoverfladen. Dette kan gøres med minimalt arbejde og indvirkning for dine brugere og tjenester. Ved at reducere angrebsområdet har hackere færre metoder til at starte et angreb mod din organisation.

Her er nogle eksempler:

- Deaktiver protokollerne POP3, IMAP og SMTP. De fleste moderne organisationer bruger ikke længere disse ældre protokoller. Du kan roligt deaktivere disse og kun tillade undtagelser efter behov.
- Reducer og bevar antallet af globale administratorer i lejeren til det absolutte minimum, der kræves. Dette reducerer direkte angrebsområdet for alle Cloud-programmer.
- Tilbagetrækning af servere og programmer, der ikke længere bruges i dit miljø.
- Implementer en proces til deaktivering og sletning af konti, der ikke længere bruges.

## <a name="protect-against-known-threats"></a>Beskyt dig mod kendte trusler

Kendte trusler omfatter malware, kompromitterede konti og phishing. Nogle beskyttelser mod disse trusler kan gennemføres hurtigt uden direkte indvirkning på dine brugere, mens andre kræver mere planlægning og brugerkurser.

|Anbefaling  |E3  |E5  |
|---------|---------|---------|
|**Konfigurer multifaktorgodkendelse, og brug anbefalede politikker for betinget adgang, herunder politikker for logonrisici**. Microsoft anbefaler og har testet et sæt politikker, der arbejder sammen for at beskytte alle skyapps, herunder Office 365 og Microsoft 365 tjenester. Se [Konfigurationer for identitets- og enhedsadgang](./office-365-security/microsoft-365-policies-configurations.md). | |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Kræv multifaktorgodkendelse for alle brugere**. Hvis du ikke har den nødvendige licens til at implementere de anbefalede politikker for betinget adgang, skal du som minimum kræve multifaktorgodkendelse for alle brugere.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|**Hæve beskyttelsesniveauet mod malware i mail**. Dit Office 365 eller Microsoft 365-miljø omfatter beskyttelse mod malware, men du kan øge denne beskyttelse ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|**Beskyt dine mails mod målrettede phishingangreb**. Hvis du har konfigureret et eller flere brugerdefinerede domæner til dit Office 365 eller Microsoft 365, kan du konfigurere målrettet beskyttelse mod phishing. Beskyttelse mod phishing, en del af Defender for Office 365, kan hjælpe med at beskytte din organisation mod ondsindede efterligningsbaserede phishingangreb og andre phishingangreb. Hvis du ikke har konfigureret et brugerdefineret domæne, behøver du ikke at gøre dette.| |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Beskyt dig mod ransomware-angreb i mails**. Ransomware fjerner adgangen til dine data ved at kryptere filer eller låse computerskærme. Den forsøger derefter at afpresse penge fra det, der sker, ved at bede om "ekstra penge", som regel i form af hacking som Bitcoin, til at returnere adgang til dine data. Du kan hjælpe med at beskytte dig mod ransomware ved at oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware, eller for at advare brugere, der modtager disse vedhæftede filer i en mail.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|**Bloker forbindelser fra lande, du ikke handler med**. Opret en politik for betinget adgang til Azure AD for at blokere eventuelle forbindelser, der kommer fra disse lande, så der effektivt oprettes en geofirewall omkring din lejer.| |![grønt afkrydsning.](../media/green-check-mark.png)|

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="De anbefalede funktioner til beskyttelse mod kendte trusler" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::


## <a name="protect-against-unknown-threats"></a>Beskyt dig mod ukendte trusler

Når du har føjet ekstra beskyttelse til dine privilegerede konti og beskytter dig mod kendte angreb, kan du forskyde din opmærksomhed mod ukendte trusler. De mere målrettede og avancerede modgangsgrupper bruger innovative og nye, ukendte metoder til at angreb organisationer. Med Microsofts enorme telemetri af data, der er indsamlet over millioner af enheder, programmer og tjenester, kan vi udføre Defender for Office 365 på Windows, Office 365 og Azure for at forhindre Zero-Day-angreb, benytte sandkassemiljøer og kontrollere gyldigheden, før du tillader adgang til dit indhold.

|Anbefaling  |E3  |E5  |
|---------|---------|---------|
|**Konfigurer Microsoft Defender for Office 365**:<br>*Pengeskab vedhæftede filer<br>* Pengeskab links    <br>*Microsoft Defender for Endpoint til SharePoint, OneDrive og Microsoft Teams<br>* antiphishing i Defender for Office 365 beskyttelse|         |![grønt afkrydsning.](../media/green-check-mark.png) |
|**Konfigurer Microsoft Defender for Endpoint funktioner**:<br>*<br>Windows Defender Antivirus* Exploit Protection <br> *Reduktion af angrebsoverfladen <br>*    Hardwarebaseret isolation <br>* Kontrolleret mappeadgang     |         |![grønt afkrydsning.](../media/green-check-mark.png) |
|**Brug Microsoft Defender for Cloud Apps til** at opdage SaaS-apps og begynde at bruge adfærdsanalyser og registrering af unormalt indhold. |         |![grønt afkrydsning.](../media/green-check-mark.png) |

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Et eksempel på de funktioner, der tilbydes af værktøjer til at beskytte dig mod ukendte trusler" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::


Yderligere anbefalinger:

- Sikre partnerkanalkommunikation, f.eks. mails, der bruger TLS.
- Åbn Teams sammenslutning til de partnere, du kommunikerer med.
- Føj ikke afsenderdomæner, individuelle afsendere eller kilde-IP'er til din tilladelsesliste, da dette gør det muligt for disse at tilsidesætte spam- og malwarekontroller – En almindelig fremgangsmåde med kunder er at tilføje deres egne accepterede domæner eller mange andre domæner, hvor der kan være rapporteret problemer med mailflow på tilladelseslisten. Tilføj ikke domæner på listen Spam- og forbindelsesfiltrering, da dette potentielt tilsidesætter alle spamkontroller.
- Aktivér udgående spammeddelelser – Aktivér udgående spammeddelelser til en distributionsliste internt til Helpdesk- eller it-administratorteamet for at rapportere, hvis nogen af de interne brugere sender spammails eksternt. Dette kan være en indikator for, at kontoen er blevet kompromitteret.
- Deaktiver Remote PowerShell for alle brugere – Remote PowerShell bruges hovedsageligt af administratorer til at få adgang til tjenester til administrative formål eller programmeringsmæssige API-adgang. Vi anbefaler, at du deaktiverer denne indstilling for brugere, der ikke er administratorer, for at undgå genvalg, medmindre de har forretningsmæssige krav om at få adgang til den.
- Bloker adgang til Microsoft Azure-administrationsportalen for alle ikke-administratorer. Du kan gøre dette ved at oprette en regel for betinget adgang for at blokere alle brugere, undtagen administratorer.

## <a name="assume-breach"></a>Antag misligholdelse

Microsoft træffer alle mulige foranstaltninger for at forhindre trusler og angreb, men vi anbefaler, at du altid arbejder under mennesker med mennesker med fokus på "Antag brud". Selvom det er lykkedes en hacker at komme ud i miljøet, skal vi sikre os, at de ikke kan eksfiltrere data eller identitetsoplysninger fra miljøet. Vi anbefaler derfor, at du aktiverer beskyttelse mod følsomme datalækager som f.eks. CPR-numre, kreditkortnumre, andre personlige oplysninger og andre fortrolige oplysninger på organisationsniveau.


|Anbefaling |E3|E5 |
|---------|---------|---------|
|**Gennemse og optimer din betingede adgang og relaterede politikker for at tilpasse dig dine målsætninger for et netværk uden tillid**. Beskyttelse mod kendte trusler omfatter implementering af et sæt [anbefalede politikker](./office-365-security/microsoft-365-policies-configurations.md). Gennemse implementeringen af disse politikker for at sikre, at du beskytter dine apps og data mod hackere, der har fået adgang til dit netværk. Den anbefalede Intune politik for beskyttelse af apps til Windows 10 aktiverer Windows Information Protection (WIP). WIP beskytter mod utilsigtede lækager af din organisations data gennem apps og tjenester som mail, sociale medier og den offentlige sky. |         |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Deaktiver ekstern videresendelse af mail**. Hackere, der får adgang til en brugers postkasse, kan stjæle din mail ved at indstille postkassen til automatisk at videresende mails. Dette kan ske, selv uden brugerens opmærksomhed. Du kan forhindre dette ved at konfigurere en regel for mailflow.|![grønt afkrydsning.](../media/green-check-mark.png) |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Deaktiver anonym ekstern kalenderdeling**. Ekstern anonym kalenderdeling er som standard tilladt. [Deaktiver kalenderdeling](/exchange/sharing/sharing-policies/modify-a-sharing-policy) for at reducere potentiel lækage af følsomme oplysninger.|![grønt afkrydsning.](../media/green-check-mark.png) |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Konfigurer politikker til forebyggelse af datatab for følsomme data**. Opret en politik til forebyggelse af datatab i Security &amp; Compliance Center for at opdage og beskytte følsomme data som f.eks. kreditkortnumre, CPR-numre og bankkontonumre. Microsoft 365 indeholder mange foruddefinerede typer af følsomme oplysninger, som du kan bruge i politikker til forebyggelse af datatab. Du kan også oprette dine egne typer af følsomme oplysninger til følsomme data, der er brugerdefineret til dit miljø. |![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|**Implementer politikker for dataklassificering og beskyttelse af oplysninger**. Implementer følsomhedsmærkater, og brug disse til at klassificere og anvende beskyttelse på følsomme data. Du kan også bruge disse navne i politikker til forebyggelse af datatab. Hvis du bruger Azure Information Protection navne, anbefaler vi, at du undgår at oprette nye navne i andre administrationscentre.|         |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Beskyt data i tredjepartsapps og -tjenester ved hjælp af Defender til skyapps**. Konfigurer politikker for Defender til skyapps for at beskytte følsomme oplysninger på tværs af skyapps fra tredjeparter, f.eks. Salesforce, Box Dropbox. Du kan bruge følsomme oplysningstyper og de følsomhedsmærkater, du har oprettet i politikkerne for Defender til skyapps, og anvende disse på tværs af dine SaaS-apps. <br><br>Microsoft Defender for Cloud Apps giver dig mulighed for at håndhæve en lang række automatiserede processer. Politikker kan indstilles til at levere kontinuerlige scanninger til overholdelse, juridiske eDiscovery-opgaver, DLP til følsomt indhold, der deles offentligt og meget mere. Defender til skyapps kan overvåge alle filtyper baseret på mere end 20 metadatafiltre (f.eks. adgangsniveau, filtype). |         |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Brug [Microsoft Defender til slutpunkt til at](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) identificere, om brugere gemmer følsomme oplysninger på deres Windows enheder**. |         |![grønt afkrydsning.](../media/green-check-mark.png)|
|**Brug [AIP-scanner til](/azure/information-protection/deploy-aip-scanner) at identificere og klassificere oplysninger på tværs af servere og filshares**. Brug AIP-rapporteringsværktøjet til at få vist resultaterne og udføre de relevante handlinger.|         |![grønt afkrydsning.](../media/green-check-mark.png)|

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="De funktioner, der anbefales til at beskytte dig mod ukendte trusler" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::


## <a name="continuous-monitoring-and-auditing"></a>Løbende overvågning og overvågning

Sidst, men ikke mindst, er Løbende overvågning og overvågning af Microsoft 365-miljøet sammen med Windows og enheder afgørende for at sikre, at du hurtigt kan registrere og afhjælpe eventuelle indtrængen. Værktøjer som Secure Score, Microsoft 365 Defender-portalen og Microsoft Intelligent Graph's avancerede analyser giver uvurderlige oplysninger til din lejer og sammenkæder store mængder trusselsintelligens og sikkerhedsdata, så du får uovertrufne trusselsbeskyttelse og -registreringer.

|Anbefaling |E3 |E5 |
|---------|---------|---------|
|Kontrollér, **at overvågningsloggen** er aktiveret.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|**Gennemse Secure Score ugentligt** – Secure score er et centralt sted til at få adgang til din virksomheds sikkerhedsstatus og udføre handlinger baseret på anbefalinger til Secure-scorer. Det anbefales at udføre denne kontrol ugentligt.|![grønt afkrydsning.](../media/green-check-mark.png)|![grønt afkrydsning.](../media/green-check-mark.png)|
|Brug **Microsoft Defender for Office 365-værktøjer**:<br>*Muligheder for trusselsundersøgelse og svar<br>*    Automatiseret undersøgelse og svar |         |![grønt afkrydsning.](../media/green-check-mark.png)|
|Brug **Microsoft Defender til slutpunkt**:<br> *[Registrering af slutpunkt og svar](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br>*    Automatiseret undersøgelse og afhjælpning Secure-score <br>*    [Avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![grønt afkrydsning.](../media/green-check-mark.png)|
|Brug **Microsoft Defender for Cloud Apps til** at registrere usædvanlig adfærd på tværs af skyapps for at identificere ransomware, kompromitterede brugere eller programmer, analysér brugen af høj risiko, og afhjulpet automatisk for at begrænse risikoen for din organisation.|         |:::image type="content" source="../media/green-check-mark.png" alt-text="Eksemplet med grøn farvet markering" lightbox="../media/green-check-mark.png":::|
|Brug **Microsoft Sentinel eller** dit aktuelle SIEM-værktøj til at overvåge for trusler på tværs af dit miljø. |         |![grønt afkrydsning.](../media/green-check-mark.png)|
|**[Installér Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)** for at overvåge og beskytte dig mod trusler, der er målrettet Active Directory i det lokale miljø miljøet.   |         |![grønt afkrydsning.](../media/green-check-mark.png) |
|Brug **Microsoft Defender for Cloud til at** overvåge for trusler på tværs af hybride og skybaserede arbejdsbelastninger. Microsoft Defender til skyen indeholder et gratis niveau af funktioner og et standardniveau af funktioner, der betales for, baseret på ressourcetimer eller transaktioner.|         |         |

Følgende diagram illustrerer disse funktioner.

:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="De anbefalede funktioner til kontinuerlig overvågning og overvågning" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::


Mest anbefalede overvågningshandlinger:

- **Gennemse Microsoft Secure Score ugentligt** – Secure score er et centralt sted til at få adgang til din lejers sikkerhedsstatus og udføre handlinger baseret på de vigtigste anbefalinger. Det anbefales at udføre denne kontrol ugentligt. Secure Score indeholder anbefalinger fra tværs af Azure AD, Intune, Defender til skyapps og Microsoft Defender for Endpoint samt Office 365.
- **Gennemse risikabelt logon ugentligt** – Brug Azure AD Administration til at gennemse risikabelt logon ugentligt. Det anbefalede regelsæt for identitet og enhedsadgang omfatter en politik til at gennemtvinge ændring af adgangskode ved risikabelt logon.  
- **Gennemgå de vigtigste malware- og phished-brugere** ugentligt – Brug Microsoft Defender for Office 365 Threat Explorer til at gennemgå de vigtigste brugere, der er målrettet malware og phish, og for at finde ud af den egentlige årsag til, hvorfor disse brugere påvirkes.
