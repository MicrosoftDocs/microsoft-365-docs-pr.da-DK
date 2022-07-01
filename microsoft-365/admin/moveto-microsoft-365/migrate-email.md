---
title: Overfør virksomhedsmail og -kalender fra Google Workspace
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
description: Få mere at vide om, hvordan du overfører mail, kontakter og kalender fra Google Workspace til Microsoft 365 til virksomheder.
ms.openlocfilehash: be7637816f80ecba3c56db644114d5ddb00caeb7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602032"
---
# <a name="migrate-business-email-and-calendar-from-google-workspace"></a>Overfør virksomhedsmail og -kalender fra Google Workspace

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

## <a name="watch-migrate-business-email-and-calendar-from-google-workspace"></a>Se: Overfør virksomhedsmail og -kalender fra Google Workspace

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198034).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4LPt6?autoplay=false]

Du kan bruge en administratordreven migrering til at Exchange Online fra Google Workspace. Du kan overføre mailen enten på én gang eller i faser. I følgende trin kan du se, hvordan du overfører maildataene på én gang. Du kan få flere oplysninger under [Udfør en G Suite-overførsel](/exchange/mailbox-migration/perform-g-suite-migration).

Migreringsprocessen tager flere trin og kan tage fra flere timer til et par dage afhængigt af mængden af data, du overfører.

### <a name="create-a-google-service-account"></a>Opret en Google Service-konto

1. Log på din Administratorkonsol for Google Workspace i en Chrome-browser på [admin.google.com](https://admin.google.com). 
1. Gå til siden [Tjenestekonti](https://console.developers.google.com/iam-admin/serviceaccounts) i en ny fane eller et nyt vindue. 
1. Vælg **Opret projekt**, navngiv projektet, og vælg **Opret**. 
1. Vælg **Opret tjenestekonto**, angiv et navn, vælg **Opret** og derefter **Udført**. 
1. Åbn menuen **Handlinger** , vælg **Rediger**, og notér det entydige id. Du skal bruge dette id senere i processen. 
1. Åbn afsnittet **Vis delegering for hele domænet** . 
1. Vælg **Aktivér delegering for hele G Suite-domænet**, angiv et produktnavn til samtykkeskærmen, og vælg **Gem**. 

    > [!NOTE]
    > Produktnavnet bruges ikke af overførselsprocessen, men er nødvendigt for at gemme i dialogboksen.     

1. Åbn menuen **Handlinger igen,** og vælg **Opret nøgle**. 
1. Vælg **JSON** og derefter **Opret**. 

     Den private nøgle gemmes i downloadmappen på din enhed.
 
1. Vælg **Luk**. 

### <a name="enable-api-usage-for-the-project"></a>Aktivér API-forbrug for projektet

1. Gå til [siden API'er](https://console.developers.google.com/apis/library). 
1. Angiv **Gmail-API** i søgelinjen.
1. Vælg den, og vælg derefter **Aktivér**.
1. Gentag denne proces for Google Kalender-API, Person-API og Kontakt-API. 

### <a name="grant-access-to-the-service-account"></a>Tildel adgang til tjenestekontoen

1. Gå tilbage til administrationskonsollen for Google Workspace. 
1. Vælg **Sikkerhed**, rul ned og åbn **API-kontrolelementer**. 
1. Rul ned, og vælg **Administrer delegering i hele domænet**.
1. Vælg **Tilføj ny** , og angiv det klient-id, du noterede tidligere.
1. Angiv derefter OAuth-områder for Google-API'er. Disse er tilgængelige på [aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#grant-access-to-the-service-account-for-your-google-tenant) i trin 5 og er:

    `https://mail.google.com/,https://www.googleapis.com/auth/calendar,https://www.google.com/m8/feeds/,https://www.googleapis.com/auth/gmail.settings.sharing`
 
1. Vælg **Godkend**. 

### <a name="create-a-sub-domain-for-mail-going-to-microsoft-365"></a>Opret et underdomæne til mail, der sendes til Microsoft 365

1. Gå tilbage til administrationskonsollen for **Google Workspace** .
1. Vælg **Domæner**, **Administrer domæner**, og **tilføj derefter et domænealias**. 
1. Angiv et domænealias som `m365.contoso.com`.
1. Vælg derefter **Fortsæt, og bekræft ejerskabet over domænet**. 

    Domænebekræftelse tager normalt kun et par minutter, men det kan tage op til 48 timer.

1. Gå til [Microsoft 365 Administration](https://admin.microsoft.com).
1. I den Microsoft 365 Administration skal du vælge **Vis alle** > **indstillinger** >  Domæner i venstre <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**navigationsrude**</a> og derefter **Tilføj domæne**. 
1. Angiv det underdomæne, du tidligere har oprettet, og vælg derefter **Brug dette domæne**. 
1. Hvis du vil oprette forbindelse til domænet, skal du vælge **Fortsæt**. 
1. Rul ned, og notér MX-posterne, CNAME-posterne og TXT-posterne. 
1. Gå tilbage til **Google-administrationskonsollen**.
1. Vælg **Domæner**, vælg **Administrer domæner**, **Bekræft detaljer** og derefter **Administrer domæne**. 
1. Vælg **DNS** i venstre navigationsrude, og rul ned til **Brugerdefinerede ressourceposter**. 
1. Åbn rullelisten med posttypen, vælg **MX**, angiv eller kopiér og indsæt de MX-postoplysninger, du tidligere har noteret, og vælg derefter **Tilføj**. 
1. Gentag processen for CNAME-posten og TXT-posten. 

    Det kan tage et stykke tid, før ændringerne træder i kraft.  

1. Vend tilbage til det sted, hvor du slap i Microsoft 365 Administration, og vælg **Fortsæt**. 

Dit domæne er nu konfigureret.  

### <a name="create-email-aliases-in-microsoft-365"></a>Opret mailaliaser i Microsoft 365

Før migreringen kan begynde, skal du oprette mailaliasser for dine brugere med det nye underdomæne. 

1. Hvis du vil starte næste trin, skal du vælge **Gå til aktive brugere** i guiden **Tilføj domæner** i Microsoft 365 Administration. 
1. Vælg en bruger, og **administrer derefter brugernavn og mail**. 
1. På rullelisten **Domæner** skal du vælge det underdomæne, du tidligere har oprettet. 
1. Angiv et brugernavn, vælg **Tilføj**, **Gem ændringer**, og luk vinduet. 

    Gentag denne proces for hver bruger. 

### <a name="start-the-migration-process"></a>Start overførselsprocessen

Når du er færdig, er du klar til at overføre. 

1. Rul ned til **Administration centre** i venstre navigationsrude <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>, og vælg **Exchange**. 
1. Under **modtagere** skal du vælge **Overførsel**, vælge **Ny**, **Overfør til Exchange Online**, vælge **G Suite-overførsel** og derefter **Næste**. 
1. Opret en CSV-fil med en liste over de postkasser, du vil overføre. Kontrollér, at filen har følgende format: 

    ```CSV
    EmailAddress
    will@fabrikaminc.net
    user123@fabrikaminc.net
    ```

      Du kan finde flere oplysninger [under aka.ms/GoogleWorkspaceMigration](/exchange/mailbox-migration/perform-g-suite-migration#start-a-g-suite-migration-batch-with-the-exchange-admin-center-eac). 

1. Vælg **Vælg fil**, naviger til CSV-filen, vælg den, vælg **Åbn** og derefter **Næste**. 
1. Kontrollér den mailadresse til administratoren, du vil bruge til test. 
1. Vælg **Vælg fil**, naviger til den JSON-fil, du oprettede tidligere (normalt i mappen Overførsler på din computer), vælg den, vælg **Åbn** og derefter **Næste**. 
1. Angiv et navn i **feltet Nyt overførselsbatchnavn**.
1. Angiv det underdomæne, du oprettede, i feltet **Destinationsleveringsdomæne** , vælg **Næste** og derefter **Ny**. 
1. Når oplysningerne er gemt, skal du vælge **OK**. 

    Du kan nu få vist status for din migrering. 

1. Når der er gået et stykke tid, skal du vælge **Opdater**, afhængigt af hvor mange brugere du overfører. 
1. Når status er ændret til **Synkroniseret**, skal du vælge **Fuldfør dette overførselsbatch** og derefter **Ja**. 
1. Når processen er fuldført, ændres din status til **Fuldført**. 
1. Hvis du vil, kan du vælge **Vis detaljer** for at få flere oplysninger om migreringen. 
1. Vælg **Luk**. 
1. Åbn Outlook for at bekræfte, at alle mails fra Google Workspace blev overført.
Du kan også gentage dette for kalenderelementer og kontakter.
