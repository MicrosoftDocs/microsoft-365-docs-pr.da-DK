---
title: Registrer kanalsignaler med kommunikationsoverholdelse
description: Få mere at vide om registrering af kanal signaler med kommunikationsoverholdelse.
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
ms.openlocfilehash: 35bd11ac88859c3e587771552a02097a2f090a44
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712878"
---
# <a name="detect-channel-signals-with-communication-compliance"></a>Registrer kanalsignaler med kommunikationsoverholdelse

Med politikker for overholdelse af kommunikation kan du vælge at scanne meddelelser på en eller flere af følgende kommunikationsplatforme som en gruppe eller som enkeltstående kilder. Oprindelige meddelelser, der er registreret på tværs af disse platforme, bevares på den oprindelige platformplacering i overensstemmelse med [organisationens politikker for opbevaring og venteposition](/microsoft-365/compliance/information-governance). Kopier af meddelelser, der bruges af politikker for overholdelse af kommunikation til analyse og undersøgelse, bevares, så længe politikken er på plads, også selvom brugerne forlader organisationen, og deres postkasser slettes. Når en kommunikationspolitik slettes, slettes kopier af meddelelser, der er knyttet til politikken også.

## <a name="microsoft-teams"></a>Microsoft Teams

Chatkommunikation i både offentlig og privat Microsoft Teams kanaler og individuelle chats kan scannes. Når brugerne er tildelt en politik for overholdelse af kommunikation med Microsoft Teams dækning valgt, overvåges chatkommunikation for brugerne automatisk på tværs af alle Microsoft Teams, hvor brugerne er medlem. Microsoft Teams medfølger automatisk til foruddefinerede politikskabeloner og vælges som standard i den brugerdefinerede politikskabelon. Teams kan det tage op til 48 timer at behandle chatsamtaler, der opfylder politikbetingelserne for kommunikation.

For private chat- og private kanaler understøtter politikker for overholdelse af kommunikation [Delte kanaler](/MicrosoftTeams/shared-channels) og Moderne scanning af vedhæftede filer. Understøttelse af delte kanaler Teams automatisk og kræver ikke yderligere konfigurationsændringer i kommunikationsoverholdelse. Følgende tabel opsummerer kommunikationsoverholdelsesfunktionsmåden, når du deler Teams med grupper og brugere:

|**Scenarie**|**Kommunikationsoverholdelsesfunktionsmåde**|
|:-----------|:------------------------------------|
| **Del en kanal med et internt team** | Politikker for overholdelse af kommunikation gælder for in-scope-brugere og alle meddelelser i den delte kanal |
| **Del en kanal med et eksternt team** | Politikker for overholdelse af kommunikation gælder for interne brugere og meddelelser i den delte kanal for den interne organisation |

Moderne vedhæftede filer er filer, der kommer [OneDrive](/onedrive/plan-onedrive-enterprise#modern-attachments) eller [SharePoint](/sharepoint/dev/solution-guidance/modern-experience-customizations) websteder, der er inkluderet i Teams meddelelser. Tekst udtrækkes automatisk fra disse vedhæftede filer til automatisk behandling og potentielle matches med aktive politikbetingelser og klassificeringer i kommunikation. Der er ikke behov for yderligere konfiguration for registrering og behandling af moderne vedhæftede filer. Tekst udtrækkes kun for vedhæftede filer, der matcher politikbetingelser. Tekst udtrækkes ikke for vedhæftede filer for meddelelser med politikoverensstemmelse, selvom den vedhæftede fil også har et politik match.

Moderne scanning af vedhæftede filer understøttes for følgende filtyper:

- Microsoft Word (.docx)
- Microsoft Excel (.xlsx)
- Microsoft PowerPoint (.pptx)
- Tekst (.txt)
- Portable Document Format (.pdf)

Udpakket tekst til Moderne vedhæftede filer er inkluderet i den tilknyttede meddelelse på **dashboardet Ventende** beskeder for en politik. Den udtrukne tekst til en vedhæftet fil navngives som navnet på den vedhæftede fil (og formatudvidelsen) .txt filtypenavnet. Eksempelvis ville den udpakkede tekst til en vedhæftet *fil medContosoBusinessPlan.docx* navn *ContosoBusinessPlan.docx.txtpå dashboardet* Ventende vigtige beskeder for  en politik.

Markér den udpakkede vedhæftede tekst for at få vist detaljerne *i visningerne* *Kilde og Almindelig* tekst. Når du har gennemset den, kan du løse den vedhæftede tekst eller udføre en handling ved hjælp af kontrolelementerne på kommandolinjen. Du har også mulighed for at downloade den vedhæftede fil til gennemsyn uden for overholdelsesprocessen for kommunikation.

Brug følgende konfigurationer til gruppeadministration til at overvåge individuelle brugerchats og kanalkommunikation i Teams:

- **For Teams til chatkommunikation: Tildel** individuelle brugere, eller tildel en [distributionsgruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) til politikken til overholdelse af kommunikation. Denne indstilling er for en-til-en- eller en-til-mange-bruger-/chatrelationer.
- **For Teams kanalkommunikation:** Tildel hver Microsoft Teams-kanal eller Microsoft 365-gruppe, du vil scanne, som indeholder en bestemt bruger, til politikken for overholdelse af kommunikation. Hvis du føjer den samme bruger til andre Microsoft Teams-kanaler eller Microsoft 365-grupper, skal du sørge for at føje disse nye kanaler og grupper til politikken for overholdelse af kommunikation. Hvis et medlem af kanalen er en overvåget bruger inden for en politik, og  indgående retning er konfigureret i en politik, skal alle meddelelser, der sendes inden for kanalen, gennemgås og mulige politik matches (selv for brugere i kanalen, der ikke eksplicit overvåges). Eksempelvis er Bruger A ejeren eller medlem af en kanal. Bruger B og Bruger C er medlemmer af den samme kanal og bruger det sprog, der passer til politikken for upassende indhold, som kun overvåger bruger A. Bruger B og Bruger C opretter politik match for samtaler inden for kanalen, selvom de ikke overvåges direkte i politikken for upassende indhold. Teams samtaler mellem bruger B og bruger C, der er uden for den kanal, der omfatter Bruger A, vil ikke være underlagt politikken for upassende indhold, der omfatter bruger A. Hvis du vil udelukke kanalmedlemmer fra overvågning, når andre medlemmer af kanalen eksplicit overvåges, skal du deaktivere indstillingen *Indgående* kommunikationsretning i den gældende politik for overholdelse af regler og standarder for kommunikation.
- **For Teams chatkommunikation med hybride** mailmiljøer: Kommunikationsoverholdelse kan overvåge chatmeddelelser for brugere for organisationer med en lokal Exchange-installation eller en ekstern mailudbyder, der har aktiveret Microsoft Teams. Du skal oprette en distributionsgruppe, som brugerne med lokale eller eksterne postkasser kan overvåge. Når du opretter en politik for overholdelse af kommunikation, skal du tildele denne distributionsgruppe  som valg for overvågede brugere og grupper i guiden til politik. Du kan finde flere oplysninger om krav og begrænsninger for aktivering af skybaseret lagring og Teams-understøttelse af lokale brugere i Søg efter [Teams-chatdata for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

## <a name="exchange-email"></a>Exchange mail

Postkasser, der hostes Exchange Online som en del af dit Microsoft 365- Office 365-abonnement, er alle berettiget til scanning af meddelelser. Exchange kan det tage op til 24 timer at behandle mails og vedhæftede filer, der svarer til politikkerne for overholdelse af regler og standarder. Understøttede typer af vedhæftede filer til overholdelse af kommunikationsreglerne er de samme som de filtyper, der [understøttes Exchange for regelinspektioner for mailflow](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

## <a name="yammer"></a>Yammer

Private meddelelser og offentlige samtaler og tilknyttede vedhæftede filer i Yammer kan scannes. Når en bruger føjes til politikken for overholdelse af kommunikation, der omfatter Yammer som en defineret kanal, medtages kommunikation på tværs af alle Yammer-communities, som brugeren er medlem af, i scanningsprocessen. Yammer kan det tage op til 24 timer at behandle chatsamtaler og vedhæftede filer, der svarer til politikbetingelserne for overholdelse af kommunikation. 

Yammer skal være i [indbygget tilstand](/yammer/configure-your-yammer-network/overview-native-mode) for politikker for overholdelse af kommunikation for at overvåge Yammer kommunikation og vedhæftede filer. I oprindelig tilstand er alle Yammer-brugere i Azure Active Directory (AAD), alle grupper Office 365 Grupper, og alle filer gemmes i SharePoint Online.

## <a name="skype-for-business-online"></a>Skype for Business Online

Chatkommunikation og tilknyttede vedhæftede filer i Skype for Business Online kan overvåges. Skype for Business det kan tage op til 24 timer at behandle onlinechats, der opfylder politikbetingelserne for kommunikation. Overvågede chatsamtaler kommer fra tidligere [samtaler, der er gemt i Skype for Business Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  

Brug følgende gruppeadministrationskonfiguration til at overvåge brugerchatkommunikation i Skype for Business Online:

- **For Skype for Business onlinechatkommunikation**: Tildel individuelle brugere, eller tildel en [distributionsgruppe](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) til politikken for overholdelse af kommunikation. Denne indstilling er for en-til-en- eller en-til-mange-bruger-/chatrelationer.

## <a name="third-party-sources"></a>Tredjepartskilder

Du kan scanne kommunikation for data, der er importeret i postkasser i din Microsoft 365-organisation fra tredjepartskilder som F.eks. [Hurtig bloomberg](archive-instant-bloomberg-data.md), [Slæk](archive-slack-data.md), [Zoom](archive-zoommeetings-data.md), SMS og mange andre. Du kan finde en komplet liste over forbindelser, der understøttes i overholdelse af kommunikation, under [Arkivér tredjepartsdata](archiving-third-party-data.md).

Du skal konfigurere en tredjepartsforbindelse for din Microsoft 365, før du kan tildele forbindelsen til en politik for overholdelse af kommunikation. Sektionen **Tredjepartskilder i guiden** til overholdelse af kommunikationspolitik viser kun aktuelt konfigurerede tredjepartsforbindelser.
