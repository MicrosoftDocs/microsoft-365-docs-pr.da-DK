---
title: Microsoft 365 BDM'er (Security for Business Decision Makers)
description: De mest almindelige trussels- og angrebsscenarier, som organisationer i øjeblikket står over for for deres Microsoft 365 miljøer, og anbefalede handlinger til afhjælpning af disse risici.
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
ms.openlocfilehash: 6a961e3d2740809eb4f3c0741277ef267db1b9ee
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935319"
---
# <a name="microsoft-365-security-for-business-decision-makers-bdms"></a>Microsoft 365 BDM'er (Security for Business Decision Makers)

I denne artikel beskrives nogle af de mest almindelige trussels- og angrebsscenarier, som organisationer i øjeblikket står over for i deres Microsoft 365 miljøer, og anbefalede handlinger til afhjælpning af disse risici. Selvom Microsoft 365 leveres med en lang række forudkonfigurerede sikkerhedsfunktioner, kræver det også, at du som kunde tager ansvar for at beskytte dine egne identiteter, data og enheder, der bruges til at få adgang til cloudtjenester. Denne vejledning blev udviklet af Kozeta Beam (Microsoft Cloud Security Architect) og Thiagaraj Sundararajan (Microsoft Senior Consultant).

Denne artikel er organiseret efter arbejdsprioritet og starter med at beskytte de konti, der bruges til at administrere de mest kritiske tjenester og aktiver, f.eks. din lejer, mail og SharePoint. Den gør det muligt at nærme sig sikkerheden på en metodisk måde og arbejder sammen med følgende regneark, så du kan spore dine fremskridt med interessenter og teams på tværs af organisationen: [Microsoft 365 sikkerhed for BDMs-regneark](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Microsoft-365-BDM-security-recommendations-spreadsheet.xlsx).

:::image type="content" source="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png" alt-text="Et eksempel på spreadhsheet for Microsoft 365 BDM-sikkerhedsanbefaling" lightbox="../downloads/microsoft-365-bdm-security-recommendations-spreadsheet-thumb.png":::

Microsoft giver dig værktøjet Secure Score i din lejer til automatisk at analysere din sikkerhedsholdning baseret på dine almindelige aktiviteter, tildele en score og give anbefalinger til forbedring af sikkerheden. Før du foretager de handlinger, der anbefales i denne artikel, skal du tage din aktuelle score og dine anbefalinger til efterretning. De handlinger, der anbefales i denne artikel, øger din score. Målet er ikke at opnå den maksimale score, men at være opmærksom på muligheder for at beskytte dit miljø på en måde, der ikke påvirker produktiviteten for dine brugere negativt. Se [Microsoft Secure Score](defender/microsoft-secure-score.md).

:::image type="content" source="../media/security/security-for-bdms-overview.png" alt-text="Trinnene til afhjælpning af risici for din virksomhed" lightbox="../media/security/security-for-bdms-overview.png":::

En ting mere, før vi kommer i gang. . . Sørg for at [aktivere overvågningsloggen](../compliance/search-the-audit-log-in-security-and-compliance.md). Du skal bruge disse data senere, hvis du har brug for at undersøge en hændelse eller et brud.

## <a name="protect-privileged-accounts"></a>Beskyt privilegerede konti

Som et første skridt anbefaler vi, at du sikrer, at kritiske konti i miljøet får et ekstra lag af beskyttelse, da disse konti har adgang til og tilladelser til at administrere og ændre kritiske tjenester og ressourcer, hvilket kan påvirke hele organisationen negativt, hvis de kompromitteres. Beskyttelse af privilegerede konti er en af de mest effektive måder at beskytte mod en hacker, der forsøger at hæve tilladelserne for en kompromitteret konto til en administrativ.

|Anbefaling  |E3 |E5  |
|---------|---------|---------|
|Gennemtving multifaktorgodkendelse (MFA) for alle administrative konti.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|Implementer Azure Active Directory (Azure AD) Privileged Identity Management (PIM) for at anvende privilegeret just-in-time-adgang til Azure AD- og Azure-ressourcer. Du kan også finde ud af, hvem der har adgang til og gennemse privilegeret adgang.|         | ![grønt flueben.](../media/green-check-mark.png)|
|Implementer privilegeret adgangsstyring for at administrere detaljeret adgangskontrol over privilegerede administratoropgaver i Office 365. |         | ![grønt flueben.](../media/green-check-mark.png)|
|Konfigurer og brug Privilegerede Access Workstations (PAW) til at administrere tjenester. Brug ikke de samme arbejdsstationer til at søge på internettet og kontrollere mails, der ikke er relateret til din administrative konto.|  !![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)::: |

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-privileged-accounts.png" alt-text="De anbefalede funktioner til beskyttelse af privilegerede konti" lightbox="../media/m365-security-bdm-illustrations-privileged-accounts.png":::

Yderligere anbefalinger:

- Sørg for, at konti, der synkroniseres fra det lokale miljø, ikke er tildelt administratorroller for cloudtjenester. Dette hjælper med at forhindre en hacker i at anvende konti i det lokale miljø for at få administrativ adgang til cloudtjenester.
- Sørg for, at tjenestekonti ikke er tildelt administratorroller. Disse konti overvåges ofte ikke og angives med adgangskoder, der ikke udløber. Start med at sikre, at AADConnect- og ADFS-tjenestekonti ikke er globale administratorer som standard.
- Fjern licenser fra administratorkonti. Medmindre der er en bestemt use case til at tildele licenser til bestemte administratorkonti, skal du fjerne licenser fra disse konti.

## <a name="reduce-the-surface-of-attack"></a>Reducer angrebsoverfladen

Det næste fokusområde er at reducere overfladen af angreb. Dette kan opnås med minimal indsats og indvirkning på dine brugere og tjenester. Ved at reducere overfladen af angreb har hackere færre måder at starte et angreb på din organisation på.

Her er nogle eksempler:

- Deaktiver POP3-, IMAP- og SMTP-protokoller. De fleste moderne organisationer bruger ikke længere disse ældre protokoller. Du kan deaktivere disse sikkert og kun tillade undtagelser efter behov.
- Reducer og bevar antallet af globale administratorer i lejeren til det absolutte minimum, der kræves. Dette reducerer direkte overfladeområdet for angreb for alle Cloud-programmer.
- Tilbagetrække servere og programmer, der ikke længere bruges i dit miljø.
- Implementer en proces til deaktivering og sletning af konti, der ikke længere bruges.

## <a name="protect-against-known-threats"></a>Beskyt mod kendte trusler

Kendte trusler omfatter malware, kompromitterede konti og phishing. Nogle beskyttelser mod disse trusler kan implementeres hurtigt uden direkte indvirkning på dine brugere, mens andre kræver mere planlægning og oplæring af brugerne.

|Anbefaling  |E3  |E5  |
|---------|---------|---------|
|**Konfigurer multifaktorgodkendelse, og brug anbefalede politikker for betinget adgang, herunder politikker for logonrisiko**. Microsoft anbefaler og har testet et sæt politikker, der arbejder sammen for at beskytte alle cloudapps, herunder Office 365 og Microsoft 365 tjenester. Se [Konfigurationer af identitets- og enhedsadgang](./office-365-security/microsoft-365-policies-configurations.md). | |![grønt flueben.](../media/green-check-mark.png)|
|**Kræv multifaktorgodkendelse for alle brugere**. Hvis du ikke har den licens, der kræves for at implementere de anbefalede politikker for betinget adgang, skal du som minimum kræve multifaktorgodkendelse for alle brugere.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|**Hæv beskyttelsesniveauet mod malware i mails**. Dit Office 365 eller Microsoft 365 miljø omfatter beskyttelse mod malware, men du kan øge denne beskyttelse ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|**Beskyt din mail mod målrettede phishingangreb**. Hvis du har konfigureret et eller flere brugerdefinerede domæner til dit Office 365 eller Microsoft 365 miljø, kan du konfigurere målrettet beskyttelse mod phishing. Beskyttelse mod phishing, der er en del af Defender for Office 365, kan hjælpe med at beskytte din organisation mod ondsindede efterligningsbaserede phishingangreb og andre phishingangreb. Hvis du ikke har konfigureret et brugerdefineret domæne, behøver du ikke at gøre dette.| |![grønt flueben.](../media/green-check-mark.png)|
|**Beskyt mod ransomware angreb i e-mail**. Ransomware fjerner adgangen til dine data ved at kryptere filer eller låse computerskærme. Det forsøger derefter at afpresse penge fra ofre ved at bede om "løsesum", som regel i form af kryptovalutaer som Bitcoin, til gengæld for at vende tilbage til dine data. Du kan hjælpe med at forsvare dig mod ransomware ved at oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware, eller for at advare brugere, der modtager disse vedhæftede filer i e-mail.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|**Bloker forbindelser fra lande, som du ikke handler med**. Opret en politik for betinget adgang i Azure AD for at blokere forbindelser, der kommer fra disse lande, og opret effektivt en geofirewall omkring din lejer.| |![grønt flueben.](../media/green-check-mark.png)|

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-known-threats.png" alt-text="De anbefalede funktioner til beskyttelse mod kendte trusler" lightbox="../media/m365-security-bdm-illustrations-known-threats.png":::


## <a name="protect-against-unknown-threats"></a>Beskyt mod ukendte trusler

Når du har føjet ekstra beskyttelse til dine privilegerede konti og beskyttelse mod kendte angreb, kan du skifte fokus på at beskytte mod ukendte trusler. De mere beslutsomme og avancerede modstandere bruger innovative og nye, ukendte metoder til at angribe organisationer. Med Microsofts store telemetri af data, der indsamles over milliarder af enheder, programmer og tjenester, kan vi udføre Defender for Office 365 på Windows, Office 365 og Azure for at forhindre Zero-Day angreb, bruge sandkassemiljøer og kontrollere gyldigheden, før du giver adgang til dit indhold.

|Anbefaling  |E3  |E5  |
|---------|---------|---------|
|**Konfigurer Microsoft Defender for Office 365**:<br>*Pengeskab vedhæftede filer<br>* Pengeskab links    <br>*Microsoft Defender for Endpoint til SharePoint, OneDrive og Microsoft Teams<br>* beskyttelse mod phishing i Defender for Office 365|         |![grønt flueben.](../media/green-check-mark.png) |
|**Konfigurer Microsoft Defender for Endpoint funktioner**:<br>*<br>beskyttelse Windows Defender Antivirus* udnyttelse <br> *Reduktion af <br>angrebsoverflade*    Hardwarebaseret isolation <br>* Adgang til kontrolleret mappe     |         |![grønt flueben.](../media/green-check-mark.png) |
|**Brug Microsoft Defender for Cloud Apps** til at finde SaaS-apps og begynde at bruge adfærdsanalyser og registrering af uregelmæssigheder. |         |![grønt flueben.](../media/green-check-mark.png) |

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-unknown-threats.png" alt-text="Et eksempel på de funktioner, der tilbydes af værktøjer til beskyttelse mod ukendte trusler" lightbox="../media/m365-security-bdm-illustrations-unknown-threats.png":::


Yderligere anbefalinger:

- Sikker partnerkanalkommunikation, f.eks. mails ved hjælp af TLS.
- Åbn kun Teams sammenslutning for de partnere, du kommunikerer med.
- Føj ikke afsenderdomæner, individuelle afsendere eller kilde-IP'er til din tilladelsesliste, da dette gør det muligt for disse at omgå spam- og malwaretjek – En almindelig praksis med kunder er at tilføje deres egne accepterede domæner eller mange andre domæner, hvor der kan være rapporteret problemer med mailflowet på listen. Tilføj ikke domæner på listen over spam- og forbindelsesfiltrering, da dette potentielt tilsidesætter alle spamtjek.
- Aktivér udgående spammeddelelser – Aktivér udgående spammeddelelser til en distributionsliste internt til helpdesk- eller it-administrationsteamet for at rapportere, hvis nogen af de interne brugere sender mails via spam eksternt. Dette kan være en indikator for, at kontoen er blevet kompromitteret.
- Deaktiver Remote PowerShell for alle brugere – Remote PowerShell bruges primært af administratorer til at få adgang til tjenester til administrative formål eller programmatisk API-adgang. Vi anbefaler, at du deaktiverer denne indstilling for brugere, der ikke er administratorer, for at undgå rekognoscering, medmindre de har et forretningskrav for at få adgang til den.
- Bloker adgang til Microsoft Azure-administrationsportalen til alle ikke-administratorer. Det kan du gøre ved at oprette en regel for betinget adgang for at blokere alle brugere undtagen administratorer.

## <a name="assume-breach"></a>Antag brud

Selvom Microsoft tager alle mulige foranstaltninger for at forhindre trusler og angreb, anbefaler vi, at du altid arbejder under tankegangen "Assume Breach". Selvom det er lykkedes en hacker at trænge ind i miljøet, skal vi sikre os, at vedkommende ikke kan eksfiltrere data- eller identitetsoplysninger fra miljøet. Derfor anbefaler vi, at du aktiverer beskyttelse mod følsomme datalækager, f.eks. CPR-numre, kreditkortnumre, andre personlige oplysninger og andre fortrolige oplysninger på organisationsniveau.


|Anbefaling |E3|E5 |
|---------|---------|---------|
|**Gennemse og optimer din betinget adgang og relaterede politikker for at tilpasse dig dine mål for et netværk, der ikke har tillid til dig**. Beskyttelse mod kendte trusler omfatter implementering af et sæt [anbefalede politikker](./office-365-security/microsoft-365-policies-configurations.md). Gennemse din implementering af disse politikker for at sikre, at du beskytter dine apps og data mod hackere, der har fået adgang til dit netværk. Den anbefalede beskyttelsespolitik for Windows 10 Intune app gør det muligt at Windows Information Protection (WIP). WIP beskytter mod utilsigtede lækager af dine organisationsdata via apps og tjenester, f.eks. mail, sociale medier og den offentlige cloud. |         |![grønt flueben.](../media/green-check-mark.png)|
|**Deaktiver videresendelse af eksterne mails**. Hackere, der får adgang til en brugers postkasse, kan stjæle din mail ved at indstille postkassen til automatisk at videresende mail. Dette kan ske selv uden brugerens opmærksomhed. Du kan forhindre, at dette sker, ved at konfigurere en regel for et mailflow.|![grønt flueben.](../media/green-check-mark.png) |![grønt flueben.](../media/green-check-mark.png)|
|**Deaktiver anonym deling af ekstern kalender**. Ekstern anonym kalenderdeling er som standard tilladt. [Deaktiver kalenderdeling](/exchange/sharing/sharing-policies/modify-a-sharing-policy) for at reducere potentielle lækager af følsomme oplysninger.|![grønt flueben.](../media/green-check-mark.png) |![grønt flueben.](../media/green-check-mark.png)|
|**Konfigurer politikker til forebyggelse af datatab for følsomme data**. Opret en Microsoft Purview-politik til forebyggelse af datatab i Security &amp; Compliance Center for at finde og beskytte følsomme data, f.eks. kreditkortnumre, cpr-numre og bankkontonumre. Microsoft 365 indeholder mange foruddefinerede følsomme oplysningstyper, som du kan bruge i politikker til forebyggelse af datatab. Du kan også oprette dine egne følsomme oplysningstyper for følsomme data, der er brugerdefineret i dit miljø. |![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|**Implementer politikker for dataklassificering og beskyttelse af oplysninger**. Implementer følsomhedsmærkater, og brug dem til at klassificere og anvende beskyttelse på følsomme data. Du kan også bruge disse mærkater i politikker til forebyggelse af datatab. Hvis du bruger Azure Information Protection-mærkater, anbefaler vi, at du undgår at oprette nye mærkater i andre administrationer.|         |![grønt flueben.](../media/green-check-mark.png)|
|**Beskyt data i tredjepartsapps og -tjenester ved hjælp af Defender for Cloud Apps**. Konfigurer Defender for Cloud Apps-politikker for at beskytte følsomme oplysninger på tværs af cloudapps fra tredjepart, f.eks. Salesforce, Box eller Dropbox. Du kan bruge typer af følsomme oplysninger og de følsomhedsmærkater, du har oprettet i Defender for Cloud Apps-politikker, og anvende disse på tværs af dine SaaS-apps. <br><br>Microsoft Defender for Cloud Apps giver dig mulighed for at gennemtvinge en lang række automatiserede processer. Politikker kan indstilles til at levere kontinuerlige overholdelsesscanninger, juridiske eDiscovery-opgaver, DLP til følsomt indhold, der deles offentligt og meget mere. Defender for Cloud Apps kan overvåge alle filtyper, der er baseret på mere end 20 metadatafiltre (f.eks. adgangsniveau, filtype). |         |![grønt flueben.](../media/green-check-mark.png)|
|**Brug [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/information-protection-in-windows-overview) til at identificere, om brugerne gemmer følsomme oplysninger på deres Windows enheder**. |         |![grønt flueben.](../media/green-check-mark.png)|
|**Brug [AIP Scanner](/azure/information-protection/deploy-aip-scanner) til at identificere og klassificere oplysninger på tværs af servere og filshares**. Brug rapporteringsværktøjet til AIP til at få vist resultaterne og udføre relevante handlinger.|         |![grønt flueben.](../media/green-check-mark.png)|

Følgende diagram illustrerer disse funktioner.
:::image type="content" source="../media/m365-security-bdm-illustrations-assume-breach.png" alt-text="De funktioner, der anbefales til beskyttelse mod ukendte trusler" lightbox="../media/m365-security-bdm-illustrations-assume-breach.png":::


## <a name="continuous-monitoring-and-auditing"></a>Løbende overvågning og overvågning

Sidst men ikke mindst er kontinuerlig overvågning og overvågning af Microsoft 365 miljø sammen med Windows og enheder afgørende for at sikre, at du hurtigt kan registrere og afhjælpe eventuelle indtrængen. Værktøjer som Secure Score, Microsoft 365 Defender Portal og Microsoft Intelligent Graph avancerede analyser giver uvurderlige oplysninger til din lejer og sammenkæder enorme mængder trusselsintelligens og sikkerhedsdata for at give dig trusselsbeskyttelse og -registrering uden sidestykke.

|Anbefaling |E3 |E5 |
|---------|---------|---------|
|Kontrollér, at **overvågningsloggen** er slået til.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|**Gennemse Secure Score ugentligt** – Sikker score er en central placering, hvor du kan få adgang til sikkerhedsstatussen for din virksomhed og udføre handlinger baseret på anbefalinger til sikker score. Det anbefales at udføre denne kontrol ugentligt.|![grønt flueben.](../media/green-check-mark.png)|![grønt flueben.](../media/green-check-mark.png)|
|Brug **Microsoft Defender for Office 365** værktøjer:<br>*Trusselsundersøgelses- og svarfunktioner<br>*    Automatiseret undersøgelse og svar |         |![grønt flueben.](../media/green-check-mark.png)|
|Brug **Microsoft Defender til slutpunkt**:<br> *[Registrering af slutpunkt og svar](/windows/security/threat-protection/microsoft-defender-atp/overview-endpoint-detection-response) <br>*    Sikker score for automatiseret undersøgelse og afhjælpning <br>*    [Avanceret jagt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) <br>|         |![grønt flueben.](../media/green-check-mark.png)|
|Brug **Microsoft Defender for Cloud Apps** til at registrere usædvanlig adfærd på tværs af cloudapps for at identificere ransomware, kompromitterede brugere eller rogue-programmer, analysere højrisikobrug og afhjælpe automatisk for at begrænse risikoen for din organisation.|         |:::image type="content" source="../media/green-check-mark.png" alt-text="Eksemplet med grøn farvet markering" lightbox="../media/green-check-mark.png":::|
|Brug **Microsoft Sentinel** eller dit aktuelle SIEM-værktøj til at overvåge trusler på tværs af dit miljø. |         |![grønt flueben.](../media/green-check-mark.png)|
|**Udrul [Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)** for at overvåge og beskytte mod trusler, der er målrettet dit Active Directory i det lokale miljø miljø.   |         |![grønt flueben.](../media/green-check-mark.png) |
|Brug **Microsoft Defender for Cloud** til at overvåge trusler på tværs af hybrid- og cloudarbejdsbelastninger. Microsoft Defender for Cloud indeholder et gratis niveau af funktioner og et standardniveau af funktioner, der betales for baseret på ressourcetimer eller transaktioner.|         |         |

Følgende diagram illustrerer disse funktioner.

:::image type="content" source="../media/m365-security-bdm-illustrations-monitoring-auditing.png" alt-text="De anbefalede funktioner til løbende overvågning og overvågning" lightbox="../media/m365-security-bdm-illustrations-monitoring-auditing.png":::


Vigtigste anbefalede overvågningshandlinger:

- **Gennemse Microsoft Secure Score ugentligt** – Sikker score er en central placering, hvor du kan få adgang til din lejers sikkerhedsstatus og udføre handlinger baseret på topanbefalinger. Det anbefales at udføre denne kontrol ugentligt. Secure Score indeholder anbefalinger fra hele Azure AD, Intune, Defender for Cloud Apps og Microsoft Defender for Endpoint samt Office 365.
- **Gennemse risikable logons ugentligt** – Brug Azure AD Administration til at gennemse risikable logons ugentligt. Det anbefalede regelsæt for identitets- og enhedsadgang indeholder en politik til gennemtvingelse af adgangskodeændring ved risikable logons.  
- **Gennemse de mest populære malware- og phish-brugere ugentligt** – Brug Microsoft Defender for Office 365 Threat Explorer til at gennemse topbrugere, der er målrettet med malware og phish, og til at finde den egentlige årsag til, hvorfor disse brugere påvirkes.
