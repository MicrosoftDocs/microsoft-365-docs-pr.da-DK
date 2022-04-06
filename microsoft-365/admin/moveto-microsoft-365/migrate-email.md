---
title: Overføre virksomhedsmail og -kalender fra Google Workspace
f1.keywords:
- NOCSH
ms.author: twerner
author: twernermsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- adminvideo
- admindeeplinkMAC
monikerRange: o365-worldwide
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan du overfører mail, kontakter og kalender fra Google Workspace Microsoft 365 til virksomheder.
ms.openlocfilehash: a5ceccfde47b5084326aae9346b1c645cef7114a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63607463"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Overføre virksomhedsmail og -kalender fra Google Workspace

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Du kan bruge en administratorbaseret overførsel til at Exchange Online fra Google Workspace. Du kan overføre mailen enten på én gang eller i faser. Følgende trin viser, hvordan du overfører maildataene på én gang. Du kan få mere at vide [under Udføre en overførsel med G Suite](/exchange/mailbox-migration/perform-g-suite-migration).

Overførselsprocessen tager adskillige trin og kan tage fra flere timer til et par dage afhængigt af mængden af data, du overfører.

## <a name="try-it"></a>Prøv det!

### <a name="create-a-google-service-account"></a>Opret en Google-tjenestekonto

1. Log på din Google Workspace-administratorkonsol via en Chrome-browser [admin.google.com](https://admin.google.com). 
1. Gå til siden Tjenestekonti i en ny [fane eller et nyt](https://console.developers.google.com/iam-admin/serviceaccounts) vindue. 
1. Vælg **Opret projekt**, navngive projektet, og vælg **Opret**. 
1. Vælg **Opret tjenestekonto**, skriv et navn, vælg **Opret og** derefter **Udført**. 
1. Åbn menuen **Handlinger** , vælg **Rediger**, og vær opmærksom på det entydige id. Du skal bruge dette id senere i processen. 
1. Åbn afsnittet **Vis delegering for hele** domænet. 
1. Vælg **Aktivér Delegering for hele G Suite-domænet**, angiv et produktnavn til samtykkeskærmen, og vælg **Gem**. 

    > [!NOTE]
    > Produktnavnet bruges ikke af overførselsprocessen, men er nødvendigt for at gemme i dialogboksen.     

1. Åbn menuen **Handlinger** igen, og vælg **Opret nøgle**. 
1. Vælg **JSON** og derefter **Opret**. 

     Den private nøgle gemmes i downloadmappen på din enhed.
 
1. Vælg **Luk**. 

### <a name="enable-api-usage-for-the-project"></a>Aktivér brug af API for projektet

1. Gå til siden [API'er](https://console.developers.google.com/apis/library). 
1. Skriv **Gmail API på søgelinjen**.
1. Markér den, og vælg derefter **Aktivér**.
1. Gentag denne proces for Google Calendar API, People API og Contacts API. 

### <a name="grant-access-to-the-service-account"></a>Give adgang til tjenestekontoen

1. Gå tilbage til Google Workspace-administrationskonsollen. 
1. Vælg **Sikkerhed**, rul ned, og åbn **API-kontrolelementer**. 
1. Rul ned, og **vælg Administrer delegering for hele domænet**.
1. Vælg **Tilføj ny,** og angiv det klient-id, du noterede dig tidligere.
1. Angiv derefter OAuth-omfangerne for Google-API'er. Disse findes på [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) trin 5 og er:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Vælg **Godkend**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Opret et underdomæne til mail, der Microsoft 365

1. Gå tilbage til **Google Workspace-administrationskonsollen** .
1. Vælg **Domæner**, **Administrer domæner og** derefter Tilføj **et domænealias**. 
1. Angiv et domænealias, f.eks `m365.contoso.com`. .
1. Vælg derefter **Fortsæt, og bekræft ejerskab af domænet**. 

    Domænebekræftelse tager normalt kun et par minutter, men det kan tage op til 48 timer.

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. I feltet Microsoft 365 Administration venstre navigation skal du vælge **Vis** >  **alle Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a> og derefter **Tilføj domæne**. 
1. Angiv det underdomæne, du tidligere har oprettet, og vælg **derefter Brug dette domæne**. 
1. Hvis du vil oprette forbindelse til domænet, skal du **vælge Fortsæt**. 
1. Rul ned, og noter dig MX-posterne, CNAME-posterne og TXT-posterne. 
1. Gå tilbage til **Google-administratorkonsollen**.
1. Vælg **Domæner**, vælg **Administrer domæner**, **Bekræft detaljer,** og vælg derefter **Administrer domæne**. 
1. I venstre navigationspanel skal du **vælge DNS** og rulle ned til **Brugerdefinerede ressourceposter**. 
1. Åbn rullemenuen Posttype, og vælg **MX**, angiv eller kopiér og indsæt de oplysninger om MX-posten, du tidligere har angivet, og vælg derefter **Tilføj**. 
1. Gentag processen for CNAME-posten og TXT-posten. 

    Det kan tage lidt tid, før ændringerne træder i kraft.  

1. Vend tilbage til det sted, hvor du slap Microsoft 365 Administration, og vælg **Fortsæt**. 

Dit domæne er nu konfigureret.  

### <a name="create-email-aliases-in-microsoft-365"></a>Opret mailaliasser i Microsoft 365

Før overførslen kan begynde, skal du oprette mailaliasser til dine brugere med det nye underdomæne. 

1. For at starte det næste trin skal **du i guiden Tilføj** domæner i Microsoft 365 Administration vælge **Gå til aktive brugere**. 
1. Vælg en bruger og derefter **Administrer brugernavn og mail**. 
1. Fra **rullelisten Domæner** skal du vælge det underdomæne, du tidligere har oprettet. 
1. Angiv et brugernavn, **vælg Tilføj**, **Gem** ændringer, og luk vinduet. 

    Gentag denne proces for hver bruger. 

### <a name="start-the-migration-process"></a>Start overførselsprocessen

Når du er færdig, er du klar til at overføre. 

1. Rul ned til Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a> **navigationslinje**, og vælg **Exchange**. 
1. Under **modtagere skal** du vælge **Overførsel**, vælge **Ny**, **Overfør Exchange Online**, vælge **G Suite-overførsel** og derefter **Næste**. 
1. Opret en CSV-fil med en liste over de postkasser, du vil overføre. Sørg for, at filen følger dette format: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Du kan finde flere [oplysninger aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Vælg **Vælg fil**, gå til CSV-filen, vælg den, vælg **Åbn**, og derefter **Næste**. 
1. Bekræft den administratormailadresse, du vil bruge til test. 
1. Vælg **Vælg fil**, gå til den JSON-fil, du oprettede tidligere (som regel i mappen Overførsler på computeren), vælg den, **vælg Åbn** og derefter **Næste**. 
1. Angiv et navn i feltet **Nyt navn på overførselsbatch**.
1. Angiv det underdomæne, du har oprettet i **feltet Destinationsleveringsdomæne** , **vælg Næste** og derefter **Ny**. 
1. Når oplysningerne er gemt, skal du vælge **OK**. 

    Du kan nu få vist status for din overførsel. 

1. Når der er gået et stykke tid, skal du vælge Opdater, afhængigt af hvor mange **brugere du overfører**. 
1. Når status er ændret til Synkroniseret, **skal du** vælge **Fuldfør denne overførselsbatch** og derefter **Ja**. 
1. Når processen er fuldført, ændres din status til **Fuldført**. 
1. Hvis du vil, kan du vælge Vis **detaljer** for at få flere oplysninger om overførslen. 
1. Vælg **Luk**. 
1. Åbn Outlook for at bekræfte, at alle mails fra Google Workspace er blevet overført.
Du kan også gentage dette for kalenderelementer og kontakter.
