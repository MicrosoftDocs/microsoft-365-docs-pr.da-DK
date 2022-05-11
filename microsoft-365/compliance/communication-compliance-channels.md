---
title: Registrer kanalsignaler med kommunikationsoverholdelse
description: Få mere at vide om registrering af kanalsignaler med overholdelse af kommunikation.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 51cf52c4729a543130eac676b8732ccd2fe0a388
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65319072"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Registrer kanalsignaler med kommunikationsoverholdelse

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Med politikker for overholdelse af kommunikation kan du vælge at scanne meddelelser på en eller flere af følgende kommunikationsplatforme som en gruppe eller som separate kilder. Oprindelige meddelelser, der registreres på tværs af disse platforme, bevares på den oprindelige platformplacering i overensstemmelse med organisationens [politikker for opbevaring og bevarelse](/microsoft-365/compliance/information-governance). Kopier af meddelelser, der bruges af politikker for kommunikation med overholdelse af angivne standarder til analyse og undersøgelse, bevares, så længe politikken er på plads, selvom brugerne forlader organisationen, og deres postkasser slettes. Når en kommunikationspolitik slettes, slettes der også kopier af meddelelser, der er knyttet til politikken.

## <a name="microsoft-teams"></a>Microsoft Teams

Chatkommunikation i både offentlige og private Microsoft Teams kanaler og individuelle chats kan scannes. Når brugere tildeles en politik for overholdelse af angivne standarder for kommunikation med Microsoft Teams dækning valgt, overvåges chatkommunikation for brugerne automatisk på tværs af alle Microsoft Teams, hvor brugerne er medlem. Microsoft Teams dækning inkluderes automatisk for foruddefinerede politikskabeloner og vælges som standard i den brugerdefinerede politikskabelon. Teams chats, der opfylder betingelserne for politikken for overholdelse af angivne standarder for kommunikation, kan det tage op til 48 timer at behandle dem.

For private chat- og private kanaler understøtter politikker for overholdelse af angivne standarder for kommunikation [delte kanaler](/MicrosoftTeams/shared-channels) og moderne scanning af vedhæftede filer. Understøttelse af delte kanaler i Teams håndteres automatisk og kræver ikke yderligere konfigurationsændringer i konfigurationen af kommunikation. I følgende tabel opsummeres funktionsmåden for overholdelse af angivne standarder for kommunikation, når Teams kanaler deles med grupper og brugere:

|**Scenario**|**Funktionsmåde for kommunikation med overholdelse af angivne standarder**|
|:-----------|:------------------------------------|
| **Del en kanal med et internt team** | Politikker for kommunikation med overholdelse af angivne standarder gælder for brugere i området og alle meddelelser i den delte kanal |
| **Del en kanal med et eksternt team** | Politikker for kommunikation med overholdelse af angivne standarder gælder for interne brugere i området og meddelelser i den delte kanal for den interne organisation |

Moderne vedhæftede filer er filer, der stammer fra [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) eller [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) websteder, der er inkluderet i Teams meddelelser. Tekst udtrækkes automatisk fra disse vedhæftede filer til automatisk behandling og potentielle match med betingelser og klassificeringer for aktiv kommunikation med overholdelse af regler og standarder. Der er ikke nogen yderligere konfiguration, der er nødvendig for moderne registrering og behandling af vedhæftede filer. Tekst udtrækkes kun for vedhæftede filer, der opfylder politikbetingelserne. Tekst udtrækkes ikke for vedhæftede filer for meddelelser med politikmatch, selvom den vedhæftede fil også har et politikmatch.

Moderne scanning af vedhæftede filer understøttes for følgende filtyper:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Tekst (.txt)
- Portable Document Format (.pdf)

Udpakket tekst til moderne vedhæftede filer er inkluderet i den tilknyttede meddelelse på dashboardet **Ventende** beskeder for en politik. Den udtrukne tekst til en vedhæftet fil er navngivet som navnet på den vedhæftede fil (og filtypenavnet) og filtypenavnet .txt. Den udtrukne tekst for en vedhæftet fil med navnet *ContosoBusinessPlan.docx* vises f.eks. som *ContosoBusinessPlan.docx.txt* i dashboardet **Ventende** beskeder for en politik.

Vælg den udtrukne vedhæftede tekst for at få vist detaljerne i *visningerne Kilde* og *Almindelig tekst* . Når du har gennemset teksten, kan du løse problemet eller udføre handlinger på teksten til den vedhæftede fil ved hjælp af kontrolelementerne på kommandolinjen. Du har også mulighed for at downloade den vedhæftede fil til gennemsyn uden for korrekturprocessen for kommunikation med overholdelse af angivne standarder.

Brug følgende konfigurationer til gruppeadministration til at overvåge individuelle brugerchats og kanalkommunikation i Teams:

- **For Teams chatkommunikation:** Tildel individuelle brugere, eller tildel en [distributionsgruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) til politikken for kommunikation med overholdelse af angivne standarder. Denne indstilling er for en til en- eller en til mange-bruger-/chatrelationer.
- **For Teams kanalkommunikation:** Tildel hver Microsoft Teams kanal eller Microsoft 365 gruppe, du vil scanne, som indeholder en bestemt bruger, til politikken for kommunikation med overholdelse af angivne standarder. Hvis du føjer den samme bruger til andre Microsoft Teams kanaler eller Microsoft 365 grupper, skal du sørge for at føje disse nye kanaler og grupper til politikken for kommunikation med overholdelse af angivne standarder. Hvis et medlem af kanalen er en overvåget bruger i en politik, og den *indgående* retning er konfigureret i en politik, kan alle meddelelser, der sendes i kanalen, gennemses, og potentielle politikforekomster (selv for brugere i kanalen, der ikke udtrykkeligt overvåges). Bruger A er f.eks. ejer eller medlem af en kanal. Bruger B og Bruger C er medlemmer af den samme kanal og bruger sprog, der matches med den upassende indholdspolitik, der kun fører tilsyn med Bruger A. Bruger B og Bruger C opretter politikkampe for samtaler i kanalen, selvom de ikke overvåges direkte i den upassende indholdspolitik. Teams samtaler mellem Bruger B og Bruger C, der er uden for kanalen, som omfatter Bruger A, vil ikke være underlagt den upassende indholdspolitik, der omfatter Bruger A. Hvis du vil udelukke kanalmedlemmer fra overvågning, når andre medlemmer af kanalen overvåges eksplicit, skal du slå indstillingen *Indgående* kommunikationsretning fra i den relevante politik for overholdelse af kommunikation.
- **For Teams chatkommunikation med hybride mailmiljøer**: Overholdelse af kommunikation kan overvåge chatbeskeder for brugere for organisationer med en Exchange udrulning i det lokale miljø eller en ekstern mailudbyder, der har aktiveret Microsoft Teams. Du skal oprette en distributionsgruppe, som brugerne med lokale eller eksterne postkasser kan overvåge. Når du opretter en politik for overholdelse af angivne standarder for kommunikation, skal du tildele denne distributionsgruppe som valg af **overvågede brugere og grupper** i politikguiden. Du kan finde flere oplysninger om kravene og begrænsningerne for aktivering af skybaseret lager og understøttelse af Teams for brugere i det lokale miljø under [Søg efter Teams chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Exchange mail

Postkasser, der hostes på Exchange Online som en del af dit Microsoft 365- eller Office 365-abonnement, er alle berettiget til meddelelsesscanning. Exchange mails og vedhæftede filer, der opfylder betingelserne for politikken for kommunikation med overholdelse af angivne standarder, kan behandle ca. 24 timer. Understøttede typer vedhæftede filer til overholdelse af kommunikation er de samme som de [filtyper, der understøttes for Exchange inspektioner af regelindhold i mailflow](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Private meddelelser og offentlige samtaler og tilknyttede vedhæftede filer i Yammer communities kan scannes. Når en bruger føjes til politikken for overholdelse af angivne standarder for kommunikation, der omfatter Yammer som en defineret kanal, medtages kommunikation på tværs af alle Yammer communities, som brugeren er medlem af, i scanningsprocessen. Yammer chats og vedhæftede filer, der opfylder betingelserne for politikken for overholdelse af angivne standarder for kommunikation, kan det tage op til 24 timer at behandle dem. 

Yammer skal være i [oprindelig tilstand](/yammer/configure-your-yammer-network/overview-native-mode), for at politikker for kommunikation med overholdelse af regler og standarder kan overvåge Yammer kommunikation og vedhæftede filer. I oprindelig tilstand er alle Yammer brugere i Azure Active Directory (AAD), alle grupper er Office 365 Grupper, og alle filer gemmes i SharePoint Online.

## <a name="skype-for-business-online"></a>Skype for Business Online

Chatkommunikation og tilknyttede vedhæftede filer i Skype for Business Online kan overvåges. Skype for Business Det kan tage op til 24 timer at behandle onlinechats, der opfylder betingelserne for politikken for overholdelse af angivne standarder for kommunikation. Overvågede chatsamtaler stammer fra [tidligere samtaler, der er gemt i Skype for Business Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  

Brug følgende konfiguration af gruppeadministration til at overvåge kommunikation med brugerchat i Skype for Business Online:

- **For Skype for Business Onlinechatkommunikation**: Tildel individuelle brugere, eller tildel en [distributionsgruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) til politikken for kommunikation med overholdelse af angivne standarder. Denne indstilling er for en til en- eller en til mange-bruger-/chatrelationer.

## <a name="third-party-sources"></a>Kilder fra tredjepart

Du kan scanne kommunikation for data, der er importeret til postkasser i din Microsoft 365 organisation, fra tredjepartskilder som [Instant Bloomberg](archive-instant-bloomberg-data.md), [Slack](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS og mange andre. Du kan se en komplet liste over de connectors, der understøttes i forbindelse med overholdelse af kommunikation, under [Arkivér tredjepartsdata](archiving-third-party-data.md).

Du skal konfigurere en tredjepartsconnector for din Microsoft 365 organisation, før du kan tildele connectoren til en politik for kommunikation med overholdelse af angivne standarder. Afsnittet **Kilder fra tredjepart** i guiden til kommunikation med overholdelse af regler og standarder viser kun aktuelt konfigurerede tredjepartsconnectors.
