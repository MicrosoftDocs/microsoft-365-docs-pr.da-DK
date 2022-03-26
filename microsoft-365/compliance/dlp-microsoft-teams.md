---
title: Forebyggelse af datatab og Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Microsoft Teams og kanaler understøtter politikker til forebyggelse af datatab (DLP).
ms.openlocfilehash: 693b71181f34e948c0456779c7207fa22861dd5f
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715339"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Forebyggelse af datatab og Microsoft Teams

Hvis din organisation har forebyggelse af datatab (DLP), kan du definere politikker, der forhindrer personer i at dele følsomme oplysninger i en Microsoft Teams-kanal eller chatsession. Her er nogle eksempler på, hvordan denne beskyttelse fungerer:

- **Eksempel 1: Beskyttelse af følsomme oplysninger i meddelelser**. Antag, at nogen forsøger at dele følsomme oplysninger i Teams chat eller kanal med gæster (eksterne brugere). Hvis du har defineret en DLP-politik for at forhindre dette, slettes meddelelser med følsomme oplysninger, der sendes til eksterne brugere. Dette sker automatisk, og inden for få sekunder, afhængigt af hvordan din DLP-politik er konfigureret.

    > [!NOTE]
    > DLP til Microsoft Teams blokerer følsomt indhold, når det deles med Microsoft Teams brugere, der har:<br/>- [gæsteadgang](/MicrosoftTeams/guest-access) i teams og kanaler; eller<br/>- [ekstern adgang](/MicrosoftTeams/manage-external-access) i møder og chatsessioner. <p>DLP for eksterne chatsessioner fungerer kun, hvis både afsenderen og modtageren er i tilstanden Kun Teams og bruger [Microsoft Teams oprindelige sammenslutning](/microsoftteams/manage-external-access). DLP til Teams blokerer ikke meddelelser i forbindelse med Skype for Business eller [](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) ikke-oprindelige sammenkædede chatsessioner.

- **Eksempel 2: Beskyttelse af følsomme oplysninger i dokumenter**. Antag, at nogen forsøger at dele et dokument med gæster i Microsoft Teams en kanal eller chat, og dokumentet indeholder følsomme oplysninger. Hvis du har defineret en DLP-politik for at forhindre dette, åbnes dokumentet ikke for disse brugere. Din DLP-politik skal SharePoint og OneDrive for at beskyttelsen kan være på plads. Dette er et eksempel på DLP til SharePoint, der vises i Microsoft Teams, og kræver derfor, at brugere har licens til Office 365 DLP (inkluderet i Office 365 E3), men kræver ikke, at brugere skal have licens til Avanceret overholdelse i Office 365.)

- **Eksempel 3: Beskyttelse af kommunikation i Teams delte kanaler**. For delte kanaler anvendes Teams på teamets DLP-politik. Lad os f.eks. sige, at der er en delt kanal, der ejes af TeamA af Contoso. TeamA har en DLP-politik P1. Du kan dele en kanal på tre måder:
    - **Del med medlem**: Du inviterer bruger1 fra Contoso til at deltage i den delte kanal uden at gøre ham til medlem af TeamA. Alle i denne delte kanal, herunder bruger1, er dækket af P1.
    - **Del med team (internt)**: Du deler kanalen med et andet teamteamB i Contoso. At et andet team kan have en anden DLP-politik, men det er ligegyldigt. P1 gælder for alle i denne delte kanal, herunder både TeamA- og TeamB-brugere.
    - **Del med team (på tværs af lejere)**: Du deler kanalen med et teamteam på Fabrikam. Fabrikam har muligvis sin egen DLP-politik, men det gør ikke noget. P1 gælder for alle i denne delte kanal, herunder brugere af TeamA (Contoso) og TeamF (Fabrikam).
 
## <a name="dlp-licensing-for-microsoft-teams"></a>DLP-licensering til Microsoft Teams

[Funktioner til forebyggelse af](dlp-learn-about-dlp.md) datatab blev udvidet til at omfatte Microsoft Teams chat- og kanalmeddelelser, **herunder private kanalmeddelelser** for:

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 Information Protection and Governance
- Microsoft 365 E5/A5/G5/F5 Overholdelse og & og overholdelse & af regler og standarder

Office 365 og Microsoft 365 E3 omfatter DLP-beskyttelse til SharePoint Online, OneDrive og Exchange Online. Dette omfatter også filer, der deles via Teams, Teams bruger SharePoint Online og OneDrive til at dele filer.

Understøttelse af DLP-beskyttelse Teams chat kræver E5.

Du kan få mere at vide om licenskrav [Microsoft 365 Tenant-Level vejledning til servicelicens](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> DLP gælder kun for de faktiske meddelelser i chat- eller kanaltråden. Aktivitetsmeddelelser – som indeholder en kort forhåndsvisning af meddelelser, der vises baseret på en brugers  indstillinger for meddelelser – er ikke inkluderet i Teams DLP. Eventuelle følsomme oplysninger, der findes i den del af meddelelsen, der vises i forhåndsvisningen, forbliver synlige i meddelelsen, selv efter DLP-politikken er blevet anvendt og fjernet følsomme oplysninger i selve meddelelsen.

## <a name="scope-of-dlp-protection"></a>Omfanget af DLP-beskyttelse

DLP-beskyttelse anvendes anderledes for Teams enheder.

|Når politikken er begrænset af |Disse Teams enheder |DLP-beskyttelse er tilgængelig|
|---------|---------|---------|
|Individuelle brugerkonti     |1:1/n chats         |Ja         |
|     |Standard- og delte kanalmeddelelser         |Nej         |
|     |Private kanalmeddelelser         |Ja         |
|Sikkerhedsgrupper/distributionslister  | 1:1/n chats         |Ja         |
|     |Standard- og delte kanalmeddelelser  |Nej         |
|     |Private kanalmeddelelser         |Ja        |
|Microsoft 365 gruppe    |1:1/n chats          |Nej         |
|     |Standard- og delte kanalmeddelelser          |Ja        |
|     |Private kanalmeddelelser|Nej| 


## <a name="policy-tips-help-educate-users"></a>Politiktip hjælper med at informere brugerne

Ligesom [DLP fungerer i Exchange-, Outlook-, Outlook på internettet](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web)-, [SharePoint Online-, OneDrive for Business](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites)- og Office-skrivebordsklienter, vises politiktip, når [](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)en handling udløses med en DLP .politik. Her er et eksempel på et politiktip:

![Meddelelse om blokeret meddelelse Teams.](../media/dlp-teams-blockedmessage-notification.png)

Her har afsenderen forsøgt at dele et CPR-nummer i en Microsoft Teams kanal. Linket **Hvad kan jeg gøre?** åbner en dialogboks, hvor afsenderen kan vælge at løse problemet. Bemærk, at afsenderen kan vælge at tilsidesætte politikken eller underrette en administrator om at gennemse og løse problemet.

![Indstillinger til løsning af blokeret meddelelse.](../media/dlp-teams-blockedmessage-possibleactions.png)

I din organisation kan du vælge at tillade brugere at tilsidesætte en DLP-politik. Når du konfigurerer dine DLP-politikker, kan du bruge standardpolitiktip eller [tilpasse politiktip](#to-customize-policy-tips) til organisationen.

Når vi går tilbage til vores eksempel, hvor en afsender har delt et CPR-nummer i en Teams-kanal, så modtageren følgende:

> [!div class="mx-imgBorder"]
> ![Meddelelse blokeret.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>Sådan tilpasser du politiktip

For at udføre denne opgave skal du have tildelt en rolle, der har tilladelse til at redigere DLP-politikker. Du kan få mere at vide [under Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Overholdelsescenter ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik for forebyggelse af datatab** > .

3. Vælg en politik, og vælg **Rediger ud for** **Politikindstillinger**.

4. Opret enten en ny regel, eller rediger en eksisterende regel for politikken.

    > [!div class="mx-imgBorder"]
    > ![Redigere en regel for en politik.](../media/dlp-teams-editrule.png)

5. På fanen **Brugerbeskeder** skal du **vælge Tilpas mailteksten** og/eller **Tilpas politiktiptekstindstillingerne** .

    > [!div class="mx-imgBorder"]
    > ![Tilpas tip til brugerbeskeder og politikker.](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. Angiv den tekst, du vil bruge til mailbeskeder og/eller politiktip, og vælg derefter **Gem**.

7. På fanen **Politikindstillinger** skal du vælge **Gem**.

Det tager ca. en time, før dine ændringer fungerer gennem dit datacenter og synkroniseres med brugerkonti.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Tilføj Microsoft Teams som en placering til eksisterende DLP-politikker

For at udføre denne opgave skal du have tildelt en rolle, der har tilladelse til at redigere DLP-politikker. Du kan få mere at vide [under Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Overholdelsescenter ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik for forebyggelse af datatab** > .

3. Vælg en politik, og kig på værdierne under **Placeringer**. Hvis du kan **Teams chat og kanalmeddelelser**, er du klar. Hvis du ikke gør det, skal du klikke på **Rediger**.

    > [!div class="mx-imgBorder"]
    > ![Placeringer for eksisterende politik.](../media/dlp-teams-editexistingpolicy.png)

4. I kolonnen **Status** skal du slå politikken for chat **og Teams kanalmeddelelser til**.

    > [!div class="mx-imgBorder"]
    > ![DLP til Teams og chats og kanaler.](../media/dlp-teams-addteamschatschannels.png)

5. Behold **standardindstillingen for** alle konti under fanen Vælg placeringer, eller vælg **Lad mig vælge bestemte placeringer**. Du kan angive:

    1. Op til 1000 individuelle konti, der kan medtages eller udelades
    1. Distributionslister og sikkerhedsgrupper, der skal medtages eller udelades. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Vælg derefter **Næste**.

7. Klik på **Gem**.

Det tager ca. en time, før dine ændringer fungerer gennem dit datacenter og synkroniseres med brugerkonti.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Definer en ny DLP-politik for Microsoft Teams

For at udføre denne opgave skal du have tildelt en rolle, der har tilladelse til at redigere DLP-politikker. Du kan få mere at vide [under Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Overholdelsescenter ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik for forebyggelse af datatab** >  > **+ Opret en politik**.

3. Vælg en [skabelon](data-loss-prevention-policies.md#dlp-policy-templates), og vælg derefter **Næste**.

    I vores eksempel har vi valgt skabelonen Personligt identificerbare oplysninger i USA.

    > [!div class="mx-imgBorder"]
    > ![Skabelon til beskyttelse af personlige oplysninger for DLP-politik.](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. Angiv et **navn og en** beskrivelse af politikken under fanen Navngive din politik, og vælg derefter **Næste**.

5. Behold **standardindstillingen for** alle konti under fanen Vælg placeringer, eller vælg **Lad mig vælge bestemte placeringer**. Du kan angive:

    1. Op til 1000 individuelle konti, der kan medtages eller udelades
    1. Distributionslister og sikkerhedsgrupper, der skal medtages eller udelades. **Dette er en offentlig prøveversionsfunktion.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

    ![DLP-politikplaceringer.](../media/dlp-teams-selectlocationsnewpolicy.png)

    > [!NOTE]
    > Hvis du vil sikre dig, at dokumenter, der indeholder følsomme oplysninger, ikke deles upassende i Teams, skal du sørge **SharePoint, at SharePoint-websteder** og **OneDrive-konti** er slået til sammen med **Teams-chat** og kanalmeddelelser.

6. På fanen **Politikindstillinger** skal du under Tilpas den **type** indhold, du vil beskytte, beholde standard simple indstillinger eller vælge **Brug** avancerede indstillinger og derefter vælge **Næste**. Hvis du vælger avancerede indstillinger, kan du oprette eller redigere regler for din politik. Se Simple indstillinger kontra avancerede indstillinger for [at få hjælp til dette](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  Gennemgå **indstillingerne under** Hvad vil du **gøre, hvis vi** registrerer følsomme oplysninger? under fanen Politikindstillinger. Her kan du vælge at beholde standardpolitiktip [og mailbeskeder](use-notifications-and-policy-tips.md) eller tilpasse dem.

    > [!div class="mx-imgBorder"]
    > ![DLP-politikindstillinger med tip og meddelelser.](../media/dlp-teams-policysettings-tipsemails.png)

    Vælg Næste, når du er færdig med at gennemse eller redigere **indstillingerne**.

8. På fanen **Politikindstillinger** under Vil du aktivere politikken eller teste ting først **?** skal du vælge, om du vil aktivere [politikken, teste](dlp-overview-plan-for-dlp.md#policy-deployment) den først eller lade den være deaktiveret for nu og derefter vælge **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Angiv, om politikken skal slås til.](../media/dlp-teams-policysettings-turnonnow.png)

9. Gennemgå **indstillingerne for den nye** politik på fanen Gennemse dine indstillinger. Vælg **Rediger** for at foretage ændringer. Vælg Opret, når du er **færdig**.

Det tager ca. en time for den nye politik at arbejde sig gennem dit datacenter og synkronisere med brugerkonti.

## <a name="prevent-external-access-to-sensitive-documents"></a>Forhindre ekstern adgang til følsomme dokumenter

For at sikre SharePoint dokumenter, der indeholder følsomme oplysninger, ikke kan tilgås af eksterne gæster enten fra SharePoint eller Teams som standard, skal du vælge følgende:

- Du kan sikre, at dokumenter er beskyttet, indtil DLP-scanninger og markerer dem som sikre at dele ved at markere [nye filer som følsomme som standard](/sharepoint/sensitive-by-default).

- Anbefalet DLP-politikstruktur

    - **Betingelser**
        - Indhold indeholder en af disse typer af følsomme oplysninger: [Markér alle relevante]
        
        - Indhold deles af Microsoft 365 personer uden for organisationen
        
          > [!div class="mx-imgBorder"]
          > ![DLP-betingelser til at registrere ekstern deling af følsomt indhold.](../media/dlp-teams-external-sharing/external-condition.png)

    - **Handlinger**
        - Begræns adgangen til indholdet for eksterne brugere
        
        - Giv brugere besked med mail og politiktip
        
        - Sende hændelsesrapporter til administratoren
        
        > [!div class="mx-imgBorder"]
        > ![DLP-handling til at blokere ekstern deling af følsomt indhold.](../media/dlp-teams-external-sharing/external-action.png)

DLP-politik i aktion, når du forsøger at dele et dokument i SharePoint, der indeholder følsomme oplysninger med en ekstern gæst:

> [!div class="mx-imgBorder"]
> ![Ekstern deling er blokeret.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)


DLP-politik i brug, når gæster forsøger at åbne et dokument Teams med blokken ekstern:

> [!div class="mx-imgBorder"]
> ![Ekstern adgang blokeret.](../media/dlp-teams-external-sharing/external-access-blocked.png)

## <a name="related-articles"></a>Relaterede artikler

- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Send mailmeddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md)
