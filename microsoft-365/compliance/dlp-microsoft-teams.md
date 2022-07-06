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
description: Microsoft Teams-chats og -kanaler understøtter DLP-politikker (Data Loss Prevention).
ms.openlocfilehash: 5d2ee7cefc23a85aec1a75fbe9fe121feacbb51f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638361"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>Forebyggelse af datatab og Microsoft Teams

Hvis din organisation har Microsoft Purview Forebyggelse af datatab (DLP), kan du definere politikker, der forhindrer personer i at dele følsomme oplysninger i en Microsoft Teams-kanal eller -chatsession. Her er nogle eksempler på, hvordan denne beskyttelse fungerer:

- **Eksempel 1: Beskyttelse af følsomme oplysninger i meddelelser**. Lad os antage, at nogen forsøger at dele følsomme oplysninger i en Teams-chat eller -kanal med gæster (eksterne brugere). Hvis du har defineret en DLP-politik for at forhindre dette, slettes meddelelser med følsomme oplysninger, der sendes til eksterne brugere. Dette sker automatisk og på få sekunder, afhængigt af hvordan din DLP-politik er konfigureret.

    > [!NOTE]
    > DLP til Microsoft Teams blokerer følsomt indhold, når det deles med De Microsoft Teams-brugere, der har:<br/>- [gæsteadgang](/MicrosoftTeams/guest-access) i teams og kanaler; Eller<br/>- [ekstern adgang](/MicrosoftTeams/manage-external-access) i møder og chatsessioner. <p>DLP til eksterne chatsessioner fungerer kun, hvis både afsenderen og modtageren er i Teams Only-tilstand og bruger [den oprindelige sammenslutning af Microsoft Teams](/microsoftteams/manage-external-access). DLP til Teams blokerer ikke meddelelser i [kompatibilitet](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) med Skype for Business eller ikke-oprindelige chatsessioner i organisationsnetværket.

- **Eksempel 2: Beskyttelse af følsomme oplysninger i dokumenter**. Lad os antage, at nogen forsøger at dele et dokument med gæster i en Microsoft Teams-kanal eller -chat, og dokumentet indeholder følsomme oplysninger. Hvis du har defineret en DLP-politik for at forhindre dette, åbnes dokumentet ikke for disse brugere. Din DLP-politik skal indeholde SharePoint og OneDrive, for at beskyttelsen kan være på plads. Dette er et eksempel på DLP til SharePoint, der vises i Microsoft Teams, og som derfor kræver, at brugerne har licens til Office 365 DLP (inkluderet i Office 365 E3), men som ikke kræver, at brugerne skal have licens til Avanceret overholdelse i Office 365.

- **Eksempel 3: Beskyttelse af kommunikation i delte Teams-kanaler**. For delte kanaler anvendes DLP-politikken for værtsteamet. Lad os f.eks. sige, at der er en delt kanal, der ejes af TeamA i Contoso. TeamA har en DLP-politik P1. Der er tre måder at dele en kanal på:
    - **Del med medlem**: Du inviterer bruger1 fra Contoso til at deltage i den delte kanal uden at gøre ham til medlem af TeamA. Alle i denne delte kanal, herunder user1, dækkes af P1.
    - **Del med teamet (internt)**: Du deler kanalen med et andet teamteamB i Contoso. At et andet team kan have en anden DLP-politik, men det betyder ikke noget. P1 gælder for alle i denne delte kanal, herunder både TeamA- og TeamB-brugere.
    - **Del med team (på tværs af lejer)**: Du deler kanalen med et teamteamf i Fabrikam. Fabrikam har muligvis sin egen DLP-politik, men det betyder ikke noget. P1 gælder for alle i denne delte kanal, herunder både TeamA-brugere (Contoso) og TeamF (Fabrikam).
 
## <a name="dlp-licensing-for-microsoft-teams"></a>DLP-licenser til Microsoft Teams

[Funktioner til forebyggelse af datatab](dlp-learn-about-dlp.md) omfatter Microsoft Teams-chat- og kanalmeddelelser, **herunder private kanalmeddelelser** til:

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 Information Protection og styring
- Microsoft 365 E5/A5/G5/F5 Compliance og F5 Security & Compliance

Office 365 og Microsoft 365 E3 omfatter DLP-beskyttelse af SharePoint Online, OneDrive og Exchange Online. Dette omfatter også filer, der deles via Teams, fordi Teams bruger SharePoint Online og OneDrive til at dele filer.

Understøttelse af DLP-beskyttelse i Teams Chat kræver E5.

Hvis du vil vide mere om licenskrav, skal [du se Licensvejledning til Microsoft 365 Tenant-Level Services](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> DLP gælder kun for de faktiske meddelelser i chat- eller kanaltråden. Aktivitetsmeddelelser – som omfatter en kort meddelelsesvisning og vises på baggrund af en brugers meddelelsesindstillinger – er **ikke** inkluderet i Teams DLP. Alle følsomme oplysninger, der findes i den del af meddelelsen, der vises i prøveversionen, forbliver synlige i meddelelsen, selv efter at DLP-politikken er anvendt, og fjernede følsomme oplysninger selve meddelelsen.

## <a name="scope-of-dlp-protection"></a>Omfanget af DLP-beskyttelse

DLP-beskyttelse anvendes forskelligt på Teams-enheder.

|Når politikken er begrænset af |Disse Teams-enheder |Vil have DLP-beskyttelse tilgængelig|
|---------|---------|---------|
|Individuelle brugerkonti     |1:1/n chats         |Ja         |
|     |Standardmeddelelser og delte kanalmeddelelser         |Nej         |
|     |Private kanalmeddelelser         |Ja         |
|Sikkerhedsgrupper/distributionslister  | 1:1/n chats         |Ja         |
|     |Standardmeddelelser og delte kanalmeddelelser  |Nej         |
|     |Private kanalmeddelelser         |Ja        |
|Microsoft 365-gruppe    |1:1/n chats          |Nej         |
|     |Standardmeddelelser og delte kanalmeddelelser          |Ja        |
|     |Private kanalmeddelelser|Nej| 


## <a name="policy-tips-help-educate-users"></a>Politiktips hjælper med at uddanne brugere

På samme måde som DLP fungerer i [Exchange, Outlook, Outlook på internettet](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web), [SharePoint Online, OneDrive for Business websteder](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites) og [Office Desktop-klienter](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs), vises politiktip, når en handling udløses med en DLP-politik. Her er et eksempel på et politiktip:

![Meddelelse om blokeret meddelelse i Teams.](../media/dlp-teams-blockedmessage-notification.png)

Her forsøgte afsenderen at dele et cpr-nummer i en Microsoft Teams-kanal. Linket **Hvad kan jeg gøre?** åbner en dialogboks, der indeholder indstillinger, som afsenderen kan bruge til at løse problemet. Bemærk, at afsenderen kan vælge at tilsidesætte politikken eller give en administrator besked om at gennemse og løse den.

![Indstillinger til løsning af blokeret meddelelse.](../media/dlp-teams-blockedmessage-possibleactions.png)

I din organisation kan du vælge at tillade brugere at tilsidesætte en DLP-politik. Når du konfigurerer dine DLP-politikker, kan du bruge standardpolitiktip eller [tilpasse politiktip](#to-customize-policy-tips) til din organisation.

Vender tilbage til vores eksempel, hvor en afsender har delt et cpr-nummer i en Teams-kanal, er dette, hvad modtageren så:

> [!div class="mx-imgBorder"]
> ![Meddelelsen er blokeret.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>Sådan tilpasser du politiktip

Hvis du vil udføre denne opgave, skal du have tildelt en rolle, der har tilladelser til at redigere DLP-politikker. Du kan få mere at vide under [Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Purview Compliance Center ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik til** **forebyggelse af** >  datatab.

3. Vælg en politik, og vælg **Rediger** ud for **Politikindstillinger**.

4. Du skal enten oprette en ny regel eller redigere en eksisterende regel for politikken.

5. Under fanen **Brugermeddelelser** skal du vælge **Tilpas mailteksten** og/eller **Tilpas tekstindstillingerne for politiktip** .

6. Angiv den tekst, du vil bruge til mailmeddelelser og/eller politiktip, og vælg derefter **Gem**.

7. Vælg **Gem** under fanen **Politikindstillinger**.

Der kan gå ca. én time, før dine ændringer fungerer gennem dit datacenter og synkroniseres med brugerkonti.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>Føj Microsoft Teams som en placering til eksisterende DLP-politikker

Hvis du vil udføre denne opgave, skal du have tildelt en rolle, der har tilladelser til at redigere DLP-politikker. Du kan få mere at vide under [Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Overholdelsescenter ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik til** **forebyggelse af** >  datatab.

3. Vælg en politik, og se på værdierne under **Placeringer**. Hvis du kan se **Teams-chat- og kanalmeddelelser**, er du klar. Hvis du ikke gør det, skal du klikke på **Rediger**.

4. I kolonnen **Status** skal du aktivere politikken for **Teams-chat og -kanalmeddelelser**.

5. Under fanen **Vælg placeringer** skal du beholde standardindstillingen for alle konti eller vælge **Lad mig vælge bestemte placeringer**. Du kan angive:

    1. Op til 1000 individuelle konti, der skal medtages eller udelades
    1. Distributionslister og sikkerhedsgrupper, der skal medtages eller udelades. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. Vælg derefter **Næste**.

7. Klik på **Gem**.

Der kan gå ca. én time, før dine ændringer fungerer gennem dit datacenter og synkroniseres med brugerkonti.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>Definer en ny DLP-politik for Microsoft Teams

Hvis du vil udføre denne opgave, skal du have tildelt en rolle, der har tilladelser til at redigere DLP-politikker. Du kan få mere at vide under [Tilladelser](data-loss-prevention-policies.md#permissions).

1. Gå til Overholdelsescenter ([https://compliance.microsoft.com](https://compliance.microsoft.com)), og log på.

2. Vælg **Politik til** >  **forebyggelse af** >  datatab **+ Opret en politik**.

3. Vælg en [skabelon](data-loss-prevention-policies.md#dlp-policy-templates), og vælg derefter **Næste**.

    I vores eksempel valgte vi skabelonen Data for personidentificerbare oplysninger i USA.

4. Angiv et navn og en beskrivelse til politikken under fanen **Navngiv din politik** , og vælg derefter **Næste**.

5. Under fanen **Vælg placeringer** skal du beholde standardindstillingen for alle konti eller vælge **Lad mig vælge bestemte placeringer**. Du kan angive:

    1. Op til 1000 individuelle konti, der skal medtages eller udelades
    1. Distributionslister og sikkerhedsgrupper, der skal medtages eller udelades. **Dette er en offentlig prøveversionsfunktion.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

 
    > [!NOTE]
    > Hvis du vil sikre dig, at dokumenter, der indeholder følsomme oplysninger, ikke deles upassende i Teams, skal du sørge for, at **SharePoint-websteder** og **OneDrive-konti** er slået til sammen med **Teams-chat- og kanalmeddelelser**.

6. Under fanen **Politikindstillinger** under **Tilpas den type indhold, du vil beskytte**, skal du beholde de enkle standardindstillinger eller vælge **Brug avancerede indstillinger** og derefter vælge **Næste**. Hvis du vælger avancerede indstillinger, kan du oprette eller redigere regler for din politik. Hvis du vil have hjælp til dette, skal du se [Enkle indstillinger i forhold til avancerede indstillinger](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  Gennemse indstillingerne under **Hvad vil du foretage dig, hvis vi registrerer følsomme oplysninger under** fanen **Politikindstillinger**? Her kan du vælge at beholde tip [til standardpolitikker og mailmeddelelser](use-notifications-and-policy-tips.md) eller tilpasse dem.



    Når du er færdig med at gennemse eller redigere indstillinger, skal du vælge **Næste**.

8. Under fanen **Politikindstillinger** under **Vil du slå politikken til eller teste ting først?**, skal du vælge, om du vil aktivere politikken, [teste den først](dlp-overview-plan-for-dlp.md#policy-deployment) eller holde den deaktiveret for nu og derefter vælge **Næste**.

9. Gennemse indstillingerne for den nye politik under fanen **Gennemse dine indstillinger** . Vælg **Rediger** for at foretage ændringer. Når du er færdig, skal du vælge **Opret**.

Der kan gå ca. én time, før den nye politik fungerer gennem dit datacenter og synkroniseres med brugerkonti.

## <a name="prevent-external-access-to-sensitive-documents"></a>Undgå ekstern adgang til følsomme dokumenter

Hvis du vil sikre, at eksterne gæster ikke kan få adgang til SharePoint-dokumenter, der indeholder følsomme oplysninger, enten fra SharePoint eller Teams som standard, skal du vælge følgende:

- Du kan sikre, at dokumenter er beskyttet, indtil DLP scanner og markerer dem som sikre at dele ved at [markere nye filer som følsomme som standard](/sharepoint/sensitive-by-default).

- Anbefalet DLP-politikstruktur

    - **Betingelser**
        - Indhold indeholder en af disse følsomme oplysningstyper: [Markér alle, der skal anvendes]
        
        - Indhold deles fra Microsoft 365 med personer uden for min organisation
        
          > [!div class="mx-imgBorder"]
          > ![DLP-betingelser til registrering af ekstern deling af følsomt indhold.](../media/dlp-teams-external-sharing/external-condition.png)

    - **Handlinger**
        - Begræns adgang til indholdet for eksterne brugere
        
        - Giv brugerne besked med mail- og politiktips
        
        - Send hændelsesrapporter til administratoren
        
        > [!div class="mx-imgBorder"]
        > ![DLP-handling til at blokere ekstern deling af følsomt indhold.](../media/dlp-teams-external-sharing/external-action.png)

DLP-politik i aktion, når der gøres forsøg på at dele et dokument i SharePoint, der indeholder følsomme oplysninger med en ekstern gæst:

> [!div class="mx-imgBorder"]
> ![Ekstern deling er blokeret.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)

<!--DLP policy in action when guest attempts to open a document in Teams with block external:
can't use the below image it contains a non-approved name.
> [!div class="mx-imgBorder"]
> ![External access blocked.](../media/dlp-teams-external-sharing/external-access-blocked.png)-->

## <a name="related-articles"></a>Relaterede artikler

- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Send mailmeddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md)
