---
title: Konfigurer Moodle LMS-plug-ins, og konfigurer dem
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Bliv klar til at integrere Moodle og Microsoft Teams ved at konfigurere Moodle LMS-plug-ins.
ms.openlocfilehash: b1188878c8d0af5041bf25bb566dc0707f4e5ad4
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859106"
---
# <a name="set-up-the-moodle-lms-plugins"></a>Konfigurer Moodle LMS-plug-ins

I denne artikel lærer du, hvordan du installerer og konfigurerer Moodle LMS-plug-ins for at inkorporere Microsoft Teams med din Moodle-oplevelse.

## <a name="prerequisites"></a>Forudsætninger

Her er forudsætningerne for at konfigurere en installeret Moodle til at arbejde med Microsoft Teams:

* Legitimationsoplysninger for Moodle-administrator.
* Azure AD administratorlegitimationsoplysninger.
* Et Azure-abonnement, hvor du kan oprette nye ressourcer.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installér Microsoft 365 Moodle-plug-ins

Moodle-integration med Microsoft Teams er baseret på åben kildekode [Microsoft 365 Moodle-plug-ins-sæt](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>Nødvendige programmer og plug-ins

Download og installér følgende elementer:

1. En [aktuel stabil version af Moodle](https://download.moodle.org/releases/latest/).

    > [!IMPORTANT]
    > Hvis du ikke har et eksisterende Moodle-websted, skal du gå til [Moodle på Azure-lageret](https://github.com/azure/moodle) og hurtigt udrulle en Moodle-forekomst og tilpasse den til dine behov.

1. Download og gem Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) og [Microsoft 365 Integration-plug-ins](https://moodle.org/plugins/local_o365) på din lokale computer.

    > [!NOTE]
    > Installation af OpenID Connect- og Microsoft 365 Integration-plug-ins er påkrævet for Teams-integrationen.
    >
    > Vi anbefaler også, at du installerer [Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) Theme-plug-in'en.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle-plug-ins

#### <a name="install-plugins"></a>Installér plug-ins

1. Download plug-ins, udpak dem, og upload til deres tilsvarende mapper.
    * Udpak OpenID Opret forbindelse-plug-in (auth_oidc) til en mappe med navnet **oidc**, og upload den til **godkendelsesmappen** i Moodle-dokumentroden.
    * Udpak Plug-in'en Microsoft 365 Integration (local_o365) til en mappe med navnet **o365**, og upload den **til den lokale** mappe i Moodle-dokumentroden.
1. Log på dit Moodle-websted som administrator, og vælg **Webstedsadministration**.
1. Ved registrering af nye plug-ins, der skal installeres, skal Moodle omdirigere dig til siden til installation af nye plug-ins. Hvis dette ikke sker, skal du på siden **Webstedsadministration** vælge **Meddelelser** under fanen **Generelt** , denne handling skal udløse installationen af plug-ins.
1. Når de nye plug-ins er installeret, viser Moodle dig en side med alle nye konfigurationer fra de installerede plug-ins. Du kan trygt springe denne side over ved at anvende standardindstillingerne. Plug-ins konfigureres i følgende trin.

## <a name="2-enable-the-openid-connect-authentication-plugin"></a>2. Aktivér godkendelses-plug-in'en OpenID Connect

For at Moodle-plug-ins kan kommunikere med Microsoft-tjenester, skal OpenID Connect-godkendelses-plug-in'en være aktiveret og konfigureret.

1. Gå til **Godkendelse** **af plug-ins** til **webstedsadministration** >  > , og vælg derefter **Administrer godkendelse**.
1. Find **OpenID** Connect-godkendelses-plug-in'en, og vælg *øjeikonet* for at aktivere det.
1. Vælg **Indstillinger** for plug-in'en for at bekræfte **godkendelses-** og **tokenslutpunkterne** .
    1. Standardværdierne skal være:
        1. Godkendelsesslutpunkt: ``https://login.microsoftonline.com/common/oauth2/authorize``.
        1. Slutpunkt for token: ``https://login.microsoftonline.com/common/oauth2/token``.
1. Registrer **omdirigerings-URI'en** til senere brug.

    > [!NOTE]
    > Det er ikke påkrævet for alle Moodle-brugere at OpenID Connect-godkendelses-plug-in'en som godkendelsesmetode. Men hvis de bruger andre godkendelsesmetoder, skal deres Moodle-konti være *forbundet* til deres tilsvarende Microsoft-konti, før de kan bruge visse funktioner i Teams-integrationen, f.eks. synkronisering af Ejerskab og medlemskab af Teams.

## <a name="3-configure-the-connection-between-the-microsoft-365-plugins-and-microsoft-services"></a>3. Konfigurer forbindelsen mellem Microsoft 365-plug-ins og Microsoft-tjenester

Du skal konfigurere forbindelsen mellem Microsoft 365-plug-ins og Microsoft-tjenester, før de kan arbejde sammen.

> [!NOTE]
> Mens du konfigurerer integrationen, skal du holde konfigurationssiden for Moodle Integration i Microsoft 365 åben i en separat browserfane, da du skal vende tilbage til dette sæt sider under hele processen.

### <a name="the-teams-for-moodle-set-up-process"></a>Konfigurationsprocessen for Teams for Moodle

1. Opret Azure-app
    1. Gå til **Plug-ins til webstedsadministration** >  >  **Lokale plug-ins**, og vælg derefter **Microsoft 365-integration**. Dette åbner konfigurationssiden for Microsoft 365 Integration.

    1. Vælg fanen **Konfiguration** på siden Konfiguration af Microsoft 365-integration.

    1. Vælg knappen **Download PowerShell Script** , og gem den som en ZIP-mappe på din lokale computer.

        > [!NOTE]
        > Når scriptet køres, oprettes der et nyt Azure AD program i Microsoft 365-lejeren, som konfigurerer de påkrævede SVAR-URL-adresser og -tilladelser, giver de påkrævede tilladelser og returnerer `AppID` og `Key`.
        >
        > PowerShell-scriptet fungerer kun på Windows-operativsystemer.

    1. Forbered PowerShell-scriptet fra ZIP-filen på følgende måde:
        1. Download og udpak `Moodle-AzureAD-Powershell.zip` filen.
        1. Åbn den udpakkede mappe.
        1. Højreklik på filen, `Moodle-AzureAD-Script.ps1` og vælg **Egenskaber**.
        1. Under fanen **Generelt** i vinduet Egenskaber skal du markere afkrydsningsfeltet `Unblock` ud for attributten **Sikkerhed** nederst i vinduet.
        1. Vælg **OK**.
        1. Kopiér mappestien til den udpakkede mappe.

    1. Kør PowerShell som administrator:
        1. I Windows skal du vælge **Start**.
        1. Type `PowerShell`.
        1. Højreklik på **Windows PowerShell**.
        1. Vælg **Kør som administrator**.

    1. Gå til den udpakkede mappe ved at skrive `cd .../.../Moodle-AzureAD-Powershell` , hvor `.../...` stien til mappen er.

    1. Udfør PowerShell-scriptet:
        1. Angiv `./Moodle-AzureAD-Script.ps1`.
        1. Når du bliver spurgt, skal du logge på din Microsoft 365-administratorkonto i pop op-vinduet.
        1. Når du bliver spurgt, skal du angive navnet på Azure AD-programmet, f.eks. Moodle- eller Moodle-plug-ins.
        1. Når du bliver spurgt, skal du angive URL-adressen til moodle-serveren.
        1. Når du bliver spurgt, skal du angive den SVAR-URL-adresse, der er kopieret fra konfigurationssiden for OpenID Connect-godkendelses-plug-in'en. Dette er i bund og grund URL-adressen på dit Moodle-websted efterfulgt af `\auth\oidc\`.
        1. Du bliver muligvis bedt om at logge på din Microsoft 365-konto igen i et pop op-vindue i processen. Dette er for at give administratorsamtykke til de tilladelser, der er føjet til appen for din organisation.
        1. Når scriptet er fuldført, skal du kopiere det **program-id (`AppID`)** og **den programnøgle(), der`Key`** genereres af scriptet, og gemme dem.

1. Angiv oplysninger om Azure-app i Moodle
    1. Gå tilbage til konfigurationssiden for OpenID Connect-godkendelses-plug-in'en.
    1. Indsæt værdien `AppID` i feltet **Program-id** og værdien `Key` i feltet **Nøgle** , og vælg derefter **Gem ændringer**.

1. Konfigurer forbindelse mellem Microsoft-plug-ins og Microsoft-tjenester
    1. Vælg fanen **Konfiguration** på siden Konfiguration af Microsoft 365-integration.
    1. I **Vælg forbindelsesmetode** skal du vælge **Programadgang** og derefter vælge **Gem ændringer** igen.
    1. Når siden er opdateret, kan du se et andet nyt afsnit **Administration samtykke & yderligere oplysninger**.
        1. Vælg **Linket Angiv Administration samtykke**, angiv dine legitimationsoplysninger til den globale Microsoft 365-administrator, og vælg derefter **Acceptér** for at tildele tilladelserne.
        1. Ud for feltet **Azure AD lejer** skal du vælge knappen **Registrer**.
        1. Ud for **den OneDrive for Business URL-adresse** skal du vælge knappen **Registrer**.
        1. Når felterne er udfyldt, skal du vælge knappen **Gem ændringer** igen.

    1. Vælg knappen **Opdater** for at bekræfte installationen. Hvis der ikke rapporteres nogen fejl i denne fase, betyder det, at Microsoft-plug-ins kan kommunikere med Microsoft-serveren via Microsoft Graph-API'er.

1. Konfigurer bruger- og kursussynkronisering
    1. Synkroniser brugere mellem Moodle-serveren og Azure AD. Afhængigt af dit miljø kan du vælge forskellige indstillinger i denne fase. Sådan kommer du i gang:
        1. På konfigurationssiden for Microsoft 365-integration skal du vælge fanen **Synkroniseringsindstillinger** .

        1. I indstillingen **Synkroniser brugere med Azure AD** skal du markere de afkrydsningsfelter, der gælder for dit miljø. Du skal vælge følgende indstillinger:  
            ✔ Opret konti i Moodle for brugere i Azure AD.
           ✔ Opdater alle konti i Moodle for brugere i Azure AD.

        1. I afsnittet **Begrænsning af oprettelse af bruger** kan du konfigurere et filter for at begrænse de Azure AD brugere, der synkroniseres til Moodle.

        > [!NOTE]
        > Det er ikke nødvendigt at aktivere brugersynkronisering. Det vil dog gøre det meget nemmere at oprette forbindelse mellem Moodle-brugere og Microsoft 365-konti.
        >
        > Brugersynkronisering udføres ved at køre **Synkroniser brugere med Azure AD** planlagte opgave.

    1. I afsnittet **Kursussynkronisering** kan du vælge **Indstillingen Til tilpasning af kursussynkronisering** for at aktivere automatisk oprettelse af Teams for nogle eller alle dine eksisterende Moodle-kurser.

        > [!NOTE]
        > Kursussynkronisering udføres ved at køre **Sync Moodle-kurserne til den planlagte opgave i Microsoft Teams** .

    1. Gem ændringerne.

    1. Hvis du vil validere synkroniseringskonfigurationen, skal du køre de planlagte opgaver manuelt for første gang og navigere til **Webstedsadministration** > **Server-opgaver** >  > **Planlagte opgaver**.

        1. Rul ned, og find opgaven **Synkroniser brugere med Azure AD**, og vælg **Kør nu**.
            1. Dette synkroniserer Azure AD brugere til dit Moodle-websted i henhold til indstillingerne for brugersynkronisering.
        1. Find derefter **Sync Moodle-kurserne til Microsoft Teams-opgaven** , og vælg **Kør nu**.
            1. Denne opgave opretter grupper for alle Moodle-kurser, hvor synkroniseringsindstillingen er slået til, og også Teams, hvis der findes en **teamejer** i kurset.
            1. Opgaven synkroniserer også Moodle-brugere, der er tilmeldt kurset, til Teams som ejere eller medlemmer.
                1. En **teamejer** er en Moodle-bruger, der
                    1. er forbundet til en Microsoft 365-konto, OG
                    2. er tilmeldt kurset, AND
                    3. `local/o365:teamowner` har egenskaben i kursuskonteksten.
                1. På samme måde er et **teammedlem** en Moodle-bruger, der
                    1. er forbundet til en Microsoft 365-konto, OG
                    2. er tilmeldt kurset, AND
                    3. `local/o365:teamember` har egenskaben i kursuskonteksten.
                1. *Standardrollen* `local/o365:teamowner` Lærer har funktionen , og standardrollen `local/o365:teammember` *Studerende* har egenskaben .

    > [!NOTE]
    > De planlagte opgaver udløses af [Moodle Cron](https://docs.moodle.org/400/en/Cron), som skal konfigureres til at køre ofte. Hver planlagt opgave kan have en standardplan, som kan tilpasses.
    >
    > * Standardplanen for synkronisering af **brugere med Azure AD** opgave er hvert minut.
    > * Standardplanen for **Sync Moodle-kurserne til Microsoft Teams-opgaven** er dagligt kl. 01.00 i standardtidszonen for Moodle-serveren.

Når plug-ins er installeret og konfigureret, kan du:

* [Udrul Moodle Assistant Bot på Azure](/microsoftteams/install-moodle-integration#step-3-deploy-the-moodle-assistant-bot-to-azure).
* [Føj Moodle-faner til Teams-klasser](/microsoftteams/install-moodle-integration#step-4-deploy-your-microsoft-teams-app).
* [Føj Teams-klasser og -møder til Moodle LMS](teams-classes-meetings-with-moodle.md).

## <a name="extra-moodle-plugin-documentation"></a>Ekstra dokumentation til Moodle-plug-in

Hvis du vil gennemse Moodles Microsoft 365-integrationsvejledninger og produktbemærkninger, kan du se disse ressourcer:

* [Microsoft 365-integrationsdokumentation på Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365).
