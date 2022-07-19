---
title: Konfigurer Moodle-plugin til Open LMS
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
description: Bliv klar til at integrere One LMS og Microsoft Teams ved at konfigurere Moodle-plug-in'en.
ms.openlocfilehash: e59d9298d61060f4d898e773cc5800d32e86bebf
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66858738"
---
# <a name="set-up-and-configure-the-moodle-plugin"></a>Konfigurer Moodle-plugin

I denne artikel lærer du, hvordan du installerer og konfigurerer Moodle-plug-in'en for at integrere Microsoft Teams med din Open LMS-oplevelse.

## <a name="prerequisites"></a>Forudsætninger

Her er forudsætningerne for at installere Moodle-plug-in'en:

* Legitimationsoplysninger for Moodle-administrator.
* Microsoft Azure Active Directory (Azure AD) administratorlegitimationsoplysninger.
* Et Azure-abonnement, hvor du kan oprette nye ressourcer.

## <a name="1-install-the-microsoft-365-moodle-plugin"></a>1. Installér Microsoft 365 Moodle-plug-in'en

Open LMS-integration i Microsoft Teams er baseret på plug-in-sættet åben kildekode [Microsoft 365 Moodle](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>Nødvendige programmer og plug-ins

Installér og download følgende elementer, før du fortsætter med installationen af Microsoft 365 Moodle-plug-in'en:

1. En [aktuel stabil version af Moodle](https://download.moodle.org/releases/latest/).
1. Download og gem Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) og [Microsoft 365 Integration-plug-ins](https://moodle.org/plugins/local_o365) på din lokale computer.

    > [!NOTE]
    > Installation af OpenID Connect- og Microsoft 365 Integration-plug-ins er påkrævet for Teams-integrationen.
    >
    > Plug-in'en [Microsoft 365 Teams-tema](https://moodle.org/plugins/theme_boost_o365teams) anbefales.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle-plug-ins

#### <a name="install-plugins"></a>Installér plug-ins

1. Download plug-ins, udpak dem, og upload til deres tilsvarende mapper. Udpak f.eks. OpenID Connect-plug-in'en (auth_oidc) til en mappe med navnet **oidc**, og upload den til **godkendelsesmappen** i moodle-dokumentroden.
2. Log på dit Moodle-websted som administrator, og vælg **Webstedsadministration**.
3. Ved registrering af nye plug-ins, der skal installeres, skal Moodle omdirigere dig til siden til installation af nye plug-ins. Hvis dette ikke sker, skal du på siden **Webstedsadministration** vælge **Meddelelser** under fanen **Generelt** , da dette skal udløse installationen af plug-ins.

    > [!IMPORTANT]
    >
    > * Hold konfigurationssiden for Moodle-plug-in'er til Microsoft 365 åben i en separat browserfane, da du skal vende tilbage til dette sæt sider under hele processen.  
    >
    > * Hvis du ikke har et eksisterende Moodle-websted, skal du gå til [Moodle på Azure-lageret](https://github.com/azure/moodle) og hurtigt udrulle en Moodle-forekomst og tilpasse den til dine behov.

#### <a name="enable-the-openid-connect-authentication-plugin"></a>Aktivér OpenID Connect-godkendelses-plug-in'en

1. Gå til **Godkendelse** **af plug-ins** til **webstedsadministration** >  > , og vælg derefter **Administrer godkendelse**.
1. Find **OpenID** Connect-godkendelses-plug-in'en, og vælg *øjeikonet* for at aktivere det.
1. Vælg **Indstillinger** for plug-in'en for at bekræfte **godkendelses-** og **tokenslutpunkterne** .
    1. Standardværdierne skal være:
        1. Godkendelsesslutpunkt: ``https://login.microsoftonline.com/common/oauth2/authorize``.
        1. Slutpunkt for token: ``https://login.microsoftonline.com/common/oauth2/token``.
1. Registrer **omdirigerings-URI'en** til senere brug.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Konfigurer forbindelsen mellem Microsoft 365-plug-ins og Azure AD

Du skal konfigurere forbindelsen mellem Microsoft 365-plug-ins og Azure AD.

### <a name="requisites"></a>Forudsætninger

Registrer Moodle som et program i din Azure AD ved hjælp af PowerShell-scriptet. Scriptet klargør følgende elementer:

* Et nyt Azure AD program til din Microsoft 365-lejer, som bruges af Microsoft 365 Moodle-plug-ins.
* Appen til din Microsoft 365-lejer konfigurerer de påkrævede URL-adresser til svar og tilladelser for den klargjorte app og returnerer `AppID` og `Key`.

Brug den genererede `AppID` side til konfiguration `Key` af Moodle-plug-ins til Microsoft 365 til at konfigurere dit Moodle-serverwebsted med Azure AD.

> [!IMPORTANT]
> Hvis du vil have mere at vide om, hvordan du registrerer din Moodle-forekomst manuelt, skal du se [Registrer din Moodle-forekomst som en applikation](https://docs.moodle.org/400/en/Microsoft_365#Azure_App_Creation_and_Configuration).

### <a name="teams-for-open-lms-setup-process"></a>Teams for Open LMS-konfigurationsproces

1. På siden Microsoft 365 Integration-plug-ins skal du vælge fanen **Installation** .

1. Vælg knappen **Download PowerShell Script** , og gem den som en ZIP-mappe på din lokale computer.

1. Forbered PowerShell-scriptet fra ZIP-filen på følgende måde:

    1. Download og udpak `Moodle-AzureAD-Powershell.zip` filen.
    1. Åbn den udpakkede mappe.
    1. Højreklik på filen, `Moodle-AzureAD-Script.ps1` og vælg **Egenskaber**.
    1. Under fanen **Generelt** i vinduet Egenskaber skal du markere afkrydsningsfeltet `Unblock` ud for attributten **Sikkerhed** nederst i vinduet.
    1. Vælg **OK**.
    1. Kopiér mappestien til den udpakkede mappe.

1. Kør PowerShell som administrator:

    1. Vælg Start.
    1. Skriv PowerShell.
    1. Højreklik på **Windows PowerShell**.
    1. Vælg **Kør som administrator**.

1. Gå til den udpakkede mappe ved at skrive `cd .../.../Moodle-AzureAD-Powershell` , hvor `.../...` stien til mappen er.

1. Udfør PowerShell-scriptet:

    1. Angiv `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Angiv `./Moodle-AzureAD-Script.ps1`.
    1. Log på din Microsoft 365-administratorkonto i pop op-vinduet.
    1. Angiv navnet på det Azure AD program, f.eks. Moodle- eller Moodle-plug-ins.
    1. Angiv URL-adressen til Moodle-serveren.
    1. Kopiér det **program-id (`AppID`)** og **den programnøgle(), der`Key`** genereres af scriptet, og gem dem.

1. Vend tilbage til administrationssiden for plug-ins,**Plug-ins** til **administration af** >  >  websted **Godkendelse** > **OpenID Opret forbindelse**.

1. Indsæt værdien `AppID` i feltet **Program-id** og værdien `Key` i feltet **Nøgle** , og vælg derefter **Gem ændringer**.

1. Gå til **Plug-ins til webstedsadministration** >  > **Lokale plug-ins**, og vælg **Microsoft 365 Integration**.

1. I **Vælg forbindelsesmetode** skal du vælge **Programadgang** og derefter vælge **Gem ændringer** igen.

1. Når siden er opdateret, kan du se et andet nyt afsnit **Administration samtykke & yderligere oplysninger**.
    1. Vælg **Linket Angiv Administration samtykke**, angiv dine legitimationsoplysninger til den globale Microsoft 365-administrator, og vælg derefter **Acceptér** for at tildele tilladelserne.
    1. Ud for feltet **Azure AD lejer** skal du vælge knappen **Registrer**.
    1. Ud for **den OneDrive for Business URL-adresse** skal du vælge knappen **Registrer**.
    1. Når felterne er udfyldt, skal du vælge knappen **Gem ændringer** igen.

1. Vælg knappen **Opdater** for at bekræfte installationen, og vælg derefter **Gem ændringer**.

1. Synkroniser brugere mellem Moodle-serveren og Azure AD. Afhængigt af dit miljø kan du vælge forskellige indstillinger i denne fase. Sådan kommer du i gang:
    1. Skift til **fanen Synkroniseringsindstillinger**.

    1. I afsnittet **Synkroniser brugere med Azure AD** skal du markere de afkrydsningsfelter, der gælder for dit miljø. Du skal vælge følgende indstillinger:  

        ✔ Opret konti i Åbn LMS for brugere i Azure AD.

        ✔ Opdater alle konti i Åbn LMS for brugere i Azure AD.

    1. I afsnittet **Begrænsning af brugeroprettelse** kan du konfigurere et filter for at begrænse de Azure AD brugere, der synkroniseres til Åbn LMS.
    1. I afsnittet **Kursussynkronisering** kan du vælge **Indstillingen Til tilpasning af kursussynkronisering** for at aktivere automatisk oprettelse af grupper og Teams for nogle eller alle dine eksisterende Open LMS-kurser.

1. Hvis du vil validere [cron-opgaver](https://docs.moodle.org/400/en/Cron) og køre dem manuelt første gang, skal du gå til **Webstedsadministration** > **serveropgaver** >  > **Planlagte opgaver**.

    1. Rul ned, og find opgaven **Synkroniser brugere med Azure AD**, og vælg **Kør nu**.
        1. Denne proces synkroniserer den Azure AD bruger til dit Open LMS-websted.
    1. Find derefter **Sync Moodle-kurserne til Microsoft Teams-opgaven** , og vælg **Kør nu**.
        1. Denne opgave opretter grupper og Teams, hvis der findes en ejer.
        1. Hvis brugeren har `local/o365:teamowner` egenskaber i kursuskonteksten, er brugeren teamejer. Hvis brugeren har `local/o365:teammember` egenskaber i kursuskonteksten, er brugeren teammedlem.  
        1. *Standardrollen* `local/o365:teamowner` Lærer har funktionen , og standardrollen `local/o365:teammember` *Studerende* har egenskaben .

    > [!NOTE]
    > Moodle [Cron](https://docs.moodle.org/400/en/Scheduled_tasks) kører i henhold til opgaveplanen. Standardplanen er én gang om dagen kl. 13:00 i serverens lokale tidszone. Cron bør dog køre oftere for at holde alt synkroniseret.

1. Gå til fanen Indstillinger for **webstedsadministration-plug-ins** >  >  **Lokale plug-ins** > **Microsoft 365 Integration** > **Teams-indstillinger**.

1. Hvis du vælger knappen **Kontrollér Moodle-indstillinger** , opdateres alle de påkrævede konfigurationer, for at Teams-integrationen kan fungere.

Når plug-ins er installeret og konfigureret, kan du:

* [Udrul Moodle Assistant Bot på Azure](/microsoftteams/install-moodle-integration#step-3-deploy-the-moodle-assistant-bot-to-azure).
* [Føj Moodle-faner til Teams-klasser](/microsoftteams/install-moodle-integration#step-4-deploy-your-microsoft-teams-app).
* [Føj Teams-klasser og -møder til Åbn LMS](open-lms-teams-classes-and-meetings.md).

## <a name="extra-moodle-plugin-documentation"></a>Ekstra dokumentation til Moodle-plug-in

Hvis du vil gennemse Open LMS's Microsoft 365-integrationsvejledninger og produktbemærkninger, skal du se disse ressourcer:

* [Microsoft 365-integrationsdokumentation på Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365).
