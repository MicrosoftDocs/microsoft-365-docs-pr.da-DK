---
title: Opret aktivitetsbeskeder
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 11/7/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MED150
- BCS160
- MET150
ms.assetid: 72bbad69-035b-4d33-b8f4-549a2743e97d
ROBOTS: NOINDEX, NOFOLLOW
description: Tilføj og administrer aktivitetsbeskeder i Microsoft 365 Overholdelsescenter så Microsoft 365 sender dig mailbeskeder, når brugere udfører bestemte aktiviteter
ms.openlocfilehash: 593c51a9d85ebb6f687a5e8573df32d4de515e6b
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63588695"
---
# <a name="create-activity-alerts"></a>Opret aktivitetsbeskeder

Du kan oprette en aktivitetsbesked, der sender dig en mail, når brugere udfører bestemte aktiviteter i Office 365. Aktivitetsbeskeder minder om at søge efter begivenheder i overvågningsloggen, bortset fra at du får tilsendt en mail, når der sker en hændelse for en aktivitet, du har oprettet en besked til.

 **Hvorfor bruge aktivitetsbeskeder i stedet for at søge i overvågningsloggen?** Der kan være visse typer aktivitet eller aktivitet, der udføres af bestemte brugere, som du virkelig gerne vil vide noget om. I stedet for at skulle huske at søge efter disse aktiviteter i overvågningsloggen, kan du bruge aktivitetsbeskeder til at få Microsoft 365 til at sende dig en mail, når brugerne udfører disse aktiviteter. Du kan f.eks. oprette en aktivitetsbesked for at give dig besked, når en bruger sletter filer i SharePoint, eller du kan oprette en besked for at give dig besked, når en bruger sletter meddelelser fra sin postkasse permanent. Mailmeddelelsen, der blev sendt til dig, indeholder oplysninger om, hvilken aktivitet der blev udført, og den bruger, der udførte den.

> [!NOTE]
> Aktivitetsbeskeder frarådes. Vi anbefaler, at du begynder at bruge påmindelsespolitikker i sikkerheds- og overholdelsescenteret i stedet for at oprette nye aktivitetsbeskeder. Beskedpolitikker giver yderligere funktionalitet, f.eks. muligheden for at oprette en beskedpolitik, der udløser en besked, når en bruger udfører en bestemt aktivitet, og visning af beskeder  på siden Vis beskeder i sikkerheds- og overholdelsescenteret. Du kan få mere at vide under [Beskedpolitikker](alert-policies.md).

## <a name="confirm-roles-and-configure-audit-logging"></a>Bekræft roller, og konfigurer overvågningslogføring

- Du skal have tildelt rollen Organisationskonfiguration i organisationens Microsoft 365 Overholdelsescenter at administrere aktivitetsbeskeder. Som standard er denne rolle tildelt rollegrupperne Overholdelsesadministrator og Organisationsadministration. Du kan finde flere oplysninger om at føje medlemmer til rollegrupper [i Giv brugere adgang til Microsoft 365 Overholdelsescenter](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

- Du (eller en anden administrator) skal først aktivere overvågningslogføring for organisationen, før du kan begynde at bruge aktivitetsbeskeder. For at gøre dette skal du blot **klikke på Start optagelse af bruger-** og administratoraktivitet **på siden Aktivitetsbeskeder** . Hvis du ikke kan se dette link, er overvågning allerede aktiveret for organisationen. Du kan også aktivere overvågning på siden Søgning **i overvågningslogfil** i Microsoft 365 Overholdelsescenter (gå til **Overvågning**). Du behøver kun at gøre dette én gang for din organisation.

- Du kan oprette beskeder for de samme aktiviteter, som du kan søge efter i overvågningsloggen. Se afsnittet [Flere oplysninger](#more-information) for at få en liste over almindelige scenarier (og den specifikke aktivitet, du skal overvåge), som du kan oprette beskeder for.

- Du kan bruge siden **Aktivitetsbeskeder** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> til kun at oprette beskeder for aktivitet, der er udført af brugere, der er angivet i organisationens adressekartotek. Du kan ikke bruge denne side til at oprette beskeder om aktiviteter, der udføres af eksterne brugere, som ikke er angivet i adressekartoteket.

## <a name="create-an-activity-alert"></a>Opret en aktivitetsbesked

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på **Tilføj ikon på siden Aktivitetsbeskeder**![.](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Ny**.

   Pop op-siden til oprettelse af en aktivitetsbesked vises.


    ![Opret en aktivitetsbesked.](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. Udfyld følgende felter for at oprette en aktivitetsbesked:

    1. **Navn** – Skriv et navn til beskeden. Navnene på beskeder skal være entydige i din organisation.

    1. **Beskrivelse** (Valgfrit) – Beskriv beskeden, f.eks. de aktiviteter og brugere, der registreres, og de brugere, som mailbeskeder sendes til. Beskrivelser giver en hurtig og nem måde at beskrive formålet med beskeden til andre administratorer.

    1. **Beskedtype** – Sørg for, at **indstillingen** Brugerdefineret er valgt.

    1. **Send denne besked, når** – Klik **på Send denne besked, når** og konfigurer derefter disse to felter:

       - **Aktiviteter** – Klik på rullelisten for at få vist de aktiviteter, som du kan oprette en besked for. Dette er den samme aktivitetsliste, der vises, når du søger i overvågningsloggen. Du kan vælge en eller flere bestemte aktiviteter, eller du kan klikke på aktivitetens gruppenavn for at markere alle aktiviteter i gruppen. Du kan finde en beskrivelse af disse aktiviteter i afsnittet "Overvågede aktiviteter" [i Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities). Når en bruger udfører nogen af de aktiviteter, du har føjet til beskeden, sendes der en mail.

       - **Brugere** – Klik på dette felt, og vælg derefter en eller flere brugere. Hvis brugerne i dette felt udfører de aktiviteter, du har føjet til **feltet Aktiviteter** , sendes der en besked. Lad feltet **Brugere være** tomt for at sende en besked, når en bruger i organisationen udfører de aktiviteter, der er angivet af beskeden.

    1. **Send** denne besked til – Klik på **Send** denne besked, og klik derefter i  feltet Modtagere, og skriv et navn for at tilføje brugere, som skal modtage en besked via mail, når en bruger  (angivet i feltet Brugere) udfører en aktivitet (angivet i **feltet** Aktiviteter). Bemærk, at du som standard er føjet til listen over modtagere. Du kan fjerne dit navn fra denne liste.

5. Klik **på Gem** for at oprette beskeden.

    Den nye besked vises på listen på siden **Aktivitetsbeskeder** .

    ![Der vises en liste over beskeder på siden Aktivitetsbeskeder.](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    Beskedens status er indstillet til **Til**. Bemærk, at de modtagere, der modtager en mail, når der sendes en besked, også vises.

## <a name="turn-off-an-activity-alert"></a>Slå en aktivitetsbesked fra

Du kan deaktivere en aktivitetsbesked, så der ikke sendes en mailmeddelelse. Når du har deaktiveret aktivitetsbeskeden, vises den stadig på listen over aktivitetsbeskeder for organisationen, og du kan stadig få vist dens egenskaber.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på den besked, du vil deaktivere, på listen over aktivitetsbeskeder for din organisation.

4. På siden **Rediger besked** skal du klikke på **til** /fra-knappen Til for at ændre status **til Fra** og derefter klikke på **Gem**.

    Status for beskeden på siderne **Aktivitetsbeskeder** er indstillet til **Fra**.

Hvis du vil slå en aktivitetsbesked til igen, skal du blot gentage  disse trin og klikke på til/fra-knappen Fra for at ændre status til **Til**.

## <a name="more-information"></a>Flere oplysninger

- Her er et eksempel på mailmeddelelsen, der sendes til de brugere, der er angivet i feltet Sendt denne besked til (og angivet under Modtagere på siden **Aktivitetsbeskeder**) i Microsoft 365 Overholdelsescenter.

    ![Eksempel på en mail, der er sendt for en aktivitetsbesked.](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- Her er nogle almindelige dokument- og mailaktiviteter, som du kan oprette aktivitetsbeskeder for. Tabellerne beskriver aktiviteten, navnet på den aktivitet, der skal oprettes en besked for, og navnet på den aktivitetsgruppe, som aktiviteten er angivet under på rullelisten Aktiviteter. Hvis du vil se en komplet liste over de aktiviteter, du kan oprette aktivitetsbeskeder for, skal du se afsnittet "Overvågede aktiviteter" [i Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities).

    > [!TIP]
    > Det kan være en ide at oprette en aktivitetsbesked for kun én aktivitet, der udføres af en hvilken som helst bruger. Eller det kan være en ide at oprette en aktivitetsbesked, der registrerer flere aktiviteter, der udføres af en eller flere brugere.

    I følgende tabel vises nogle almindelige dokumentrelaterede aktiviteter i SharePoint eller OneDrive for Business.

    | Når en bruger gør dette... | Opret en besked for denne aktivitet | Gruppen Aktivitet |
    |:-----|:-----|:-----|
    |Få en visning af et dokument på et websted.  |Åbnet fil  |Fil- og mappeaktiviteter  |
    |Redigerer eller ændrer et dokument.  |Ændret fil  |Fil- og mappeaktiviteter  |
    |Deler et dokument med en bruger uden for organisationen.  |Del fil, mappe eller websted  <br/> Og  <br/> Invitation til deling oprettet  <br/> Få mere at vide under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).  |Aktiviteter for anmodning om deling og adgang  |
    |Uploader eller downloader et dokument.  |Uploadet fil  <br/> Og/eller  <br/> Downloadet fil  |Fil- og mappeaktiviteter  |
    |Ændrer adgangstilladelserne til et websted.  |Webstedstilladelser ændret  |Aktiviteter for webstedsadministration  |

    I følgende tabel vises nogle almindelige mailrelaterede aktiviteter i Exchange Online.

    | Når en bruger gør dette... | Opret en besked for denne aktivitet | Gruppen Aktivitet |
    |:-----|:-----|:-----|
    |Sletter (fjerner) en mail fra postkassen permanent.  |Meddelelser fjernet fra postkasse  | Exchange postkasseaktiviteter  |
    |Sender en mail fra en delt postkasse.  |Meddelelse sendt ved hjælp af Send som-tilladelser  <br/> Og  <br/> Meddelelse sendt ved hjælp af Send på vegne af-tilladelser  | Exchange postkasseaktiviteter  |

- Du kan også bruge Cmdlet'er **New-ActivityAlert** og **Set-ActivityAlert** i Security & Compliance Center PowerShell til at oprette og redigere aktivitetsbeskeder. Husk følgende, hvis du bruger disse cmdlet'er til at oprette eller redigere aktivitetsbeskeder:

  - Hvis du bruger en cmdlet til at føje en aktivitet til beskeden, der ikke er angivet på rullelisten Aktiviteter, vises der en meddelelse på egenskabssiden for beskeden, hvor der står "Denne besked har brugerdefinerede handlinger, der ikke vises i vælgeren".

  - En god grund til at bruge cmdlet'erne til at oprette eller redigere en aktivitetsbesked er at sende mailbeskeder til en person uden for organisationen. Denne eksterne bruger vises på listen over modtagere af beskeden. Men hvis du fjerner denne eksterne bruger fra beskeden, kan den pågældende bruger ikke føjes til beskeden igen ved hjælp af **siden Rediger** besked. Du er nødt til at tilføje den eksterne bruger igen ved hjælp af cmdlet'en **Set-ActivityAlert** eller bruge **New-ActivityAlert-cmdlet'en** til at tilføje den samme (eller en anden) eksterne bruger til en ny besked.
