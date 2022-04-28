---
title: Opret aktivitetsbeskeder
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Tilføj og administrer aktivitetsbeskeder på Microsoft Purview-overholdelsesportalen, så Microsoft 365 sender dig mailmeddelelser, når brugerne udfører bestemte aktiviteter
ms.openlocfilehash: 99cbbe4a03047b5cf8ef366a228fc78fe9dfbda1
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097002"
---
# <a name="create-activity-alerts"></a>Opret aktivitetsbeskeder

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan oprette en aktivitetsbesked, der sender dig en mailmeddelelse, når brugerne udfører bestemte aktiviteter i Office 365. Aktivitetsbeskeder svarer til at søge efter hændelser i overvågningsloggen, bortset fra at du får tilsendt en mail, når der sker en hændelse for en aktivitet, som du har oprettet en besked for.

 **Hvorfor bruge aktivitetsbeskeder i stedet for at søge i overvågningsloggen?** Der kan være visse typer aktiviteter eller aktiviteter, der udføres af bestemte brugere, som du virkelig vil vide noget om. I stedet for at skulle huske at søge i overvågningsloggen efter disse aktiviteter kan du bruge aktivitetsbeskeder til at få Microsoft 365 sende dig en mail, når brugerne udfører disse aktiviteter. Du kan f.eks. oprette en aktivitetsbesked for at give dig besked, når en bruger sletter filer i SharePoint, eller du kan oprette en besked for at give dig besked, når en bruger sletter meddelelser permanent fra sin postkasse. Den mailmeddelelse, der sendes til dig, indeholder oplysninger om, hvilken aktivitet der blev udført, og den bruger, der udførte den.

> [!NOTE]
> Aktivitetsbeskeder frarådes. Vi anbefaler, at du begynder at bruge beskedpolitikker i Security and Compliance Center i stedet for at oprette nye aktivitetsbeskeder. Politikker for beskeder indeholder yderligere funktionalitet, f.eks. muligheden for at oprette en beskedpolitik, der udløser en besked, når en bruger udfører en angivet aktivitet, og visning af beskeder på siden **Vis beskeder** i Sikkerheds- og overholdelsescenter. Du kan få flere oplysninger under [Beskedpolitikker](alert-policies.md).

## <a name="confirm-roles-and-configure-audit-logging"></a>Bekræft roller, og konfigurer overvågningslogføring

- Du skal være tildelt rollen Organisationskonfiguration på Microsoft Purview-overholdelsesportalen for at administrere aktivitetsbeskeder. Denne rolle tildeles som standard til rollegrupperne Overholdelsesadministrator og Organisationsadministration. Du kan få flere oplysninger om, hvordan du føjer medlemmer til rollegrupper, under [Giv brugere adgang til Microsoft Purview-overholdelsesportalen](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

- Du (eller en anden administrator) skal først aktivere overvågningslogføring for din organisation, før du kan begynde at bruge aktivitetsbeskeder. Det gør du ved at klikke på **Start optagelse af bruger- og administratoraktivitet** på siden **Aktivitetsbeskeder** . Hvis du ikke kan se dette link, er overvågning allerede slået til for din organisation. Du kan også aktivere overvågning på **søgesiden Overvågningslog** på overholdelsesportalen (gå til **Overvågning**). Det skal du kun gøre én gang for din organisation.

- Du kan oprette beskeder for de samme aktiviteter, som du kan søge efter i overvågningsloggen. Se afsnittet [Flere oplysninger](#more-information) for at få en liste over almindelige scenarier (og den specifikke aktivitet, der skal overvåges), som du kan oprette beskeder for.

- Du kan bruge siden **Aktivitetsbeskeder** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> til kun at oprette beskeder for aktiviteter, der udføres af brugere, der er angivet i organisationens adressekartotek. Du kan ikke bruge denne side til at oprette beskeder for aktiviteter, der udføres af eksterne brugere, som ikke er angivet i adressekartoteket.

## <a name="create-an-activity-alert"></a>Opret en aktivitetsbesked

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på Tilføj ikon på ![siden **Aktivitetsbeskeder**.](../media/8ee52980-254b-440b-99a2-18d068de62d3.gif) **Ny**.

   Pop op-siden til oprettelse af en aktivitetsbesked vises.


    ![Opret en aktivitetsbesked.](../media/53888bd5-9fa2-4398-8ccc-1a9dc72517ac.png)

4. Udfyld følgende felter for at oprette en aktivitetsbesked:

    1. **Name** – Skriv et navn til beskeden. Beskednavne skal være entydige i din organisation.

    1. **Beskrivelse** (valgfrit) – Beskriv beskeden, f.eks. de aktiviteter og brugere, der spores, og de brugere, som mailmeddelelser sendes til. Beskrivelser giver en hurtig og nem måde at beskrive formålet med beskeden til andre administratorer på.

    1. **Beskedtype** – Kontrollér, at indstillingen **Brugerdefineret** er valgt.

    1. **Send denne besked, når** – Klik på **Send denne besked, når** og konfigurer derefter disse to felter:

       - **Aktiviteter** – Klik på rullelisten for at få vist de aktiviteter, du kan oprette en besked for. Dette er den samme aktivitetsliste, der vises, når du søger i overvågningsloggen. Du kan vælge en eller flere specifikke aktiviteter, eller du kan klikke på navnet på aktivitetsgruppen for at vælge alle aktiviteter i gruppen. Du kan finde en beskrivelse af disse aktiviteter i afsnittet "Overvågede aktiviteter" i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities). Når en bruger udfører en af de aktiviteter, du har føjet til beskeden, sendes der en mail.

       - **Brugere** – Klik på dette felt, og vælg derefter en eller flere brugere. Hvis brugerne i dette felt udfører de aktiviteter, du har føjet til feltet **Aktiviteter** , sendes der en besked. Lad feltet **Brugere** være tomt for at sende en besked, når en bruger i organisationen udfører de aktiviteter, der er angivet i beskeden.

    1. **Send denne besked til** – Klik på **Send denne besked**, klik derefter i feltet **Modtagere** , og skriv et navn for at tilføje brugere, der modtager en mailmeddelelse, når en bruger (angivet i feltet **Brugere** ) udfører en aktivitet (angivet i feltet **Aktiviteter** ). Bemærk, at du som standard er føjet til listen over modtagere. Du kan fjerne dit navn fra denne liste.

5. Klik på **Gem** for at oprette beskeden.

    Den nye besked vises på listen på siden **Aktivitetsbeskeder** .

    ![Der vises en liste over beskeder på siden Aktivitetsbeskeder.](../media/02b774f2-1719-41de-bbc9-5e5b7576f335.png)

    Status for beskeden er angivet til **Til**. Bemærk, at de modtagere, der modtager en mailmeddelelse, når der sendes en besked, også vises.

## <a name="turn-off-an-activity-alert"></a>Slå en aktivitetsbesked fra

Du kan slå en aktivitetsbesked fra, så der ikke sendes en mailmeddelelse. Når du har slået aktivitetsbeskeden fra, vises den stadig på listen over aktivitetsbeskeder for din organisation, og du kan stadig få vist dens egenskaber.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på den besked, du vil slå fra, på listen over aktivitetsbeskeder for din organisation.

4. På siden **Rediger besked** skal du klikke på til/fra-knappen **Til** for at ændre status til **Fra** og derefter klikke på **Gem**.

    Status for beskeden på siderne **aktivitetsbeskeder** er angivet til **Fra**.

Hvis du vil slå en aktivitetsbesked til igen, skal du blot gentage disse trin og klikke på til/ **fra-knappen** for at ændre status til **Til**.

## <a name="more-information"></a>Flere oplysninger

- Her er et eksempel på den mailmeddelelse, der sendes til de brugere, der er angivet i feltet Sendt denne besked til (og angivet under **Modtagere** på siden **Aktivitetsbeskeder** ) på overholdelsesportalen.

    ![Eksempel på en mailmeddelelse, der er sendt for en aktivitetsbesked.](../media/a5f91611-fae6-4fe9-82f5-58521a2e2541.png)

- Her er nogle almindelige dokument- og mailaktiviteter, som du kan oprette aktivitetsbeskeder for. I tabellerne beskrives aktiviteten, navnet på den aktivitet, der skal oprettes en besked for, og navnet på den aktivitetsgruppe, som aktiviteten er angivet under på rullelisten **Aktiviteter** . Hvis du vil se en komplet liste over de aktiviteter, du kan oprette aktivitetsbeskeder for, skal du se afsnittet "Overvågede aktiviteter" i [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#audited-activities).

    > [!TIP]
    > Det kan være en god idé at oprette en aktivitetsbesked for kun én aktivitet, der udføres af en hvilken som helst bruger. Det kan også være en god idé at oprette en aktivitetsbesked, der sporer flere aktiviteter udført af en eller flere brugere.

    I følgende tabel vises nogle almindelige dokumentrelaterede aktiviteter i SharePoint eller OneDrive for Business.

    | Når en bruger gør dette... | Opret en besked for denne aktivitet | Aktivitetsgruppe |
    |:-----|:-----|:-----|
    |Viser et dokument på et websted.  |Åbnet fil  |Fil- og mappeaktiviteter  |
    |Redigerer eller ændrer et dokument.  |Ændret fil  |Fil- og mappeaktiviteter  |
    |Deler et dokument med en bruger uden for din organisation.  |Del fil, mappe eller websted  <br/> Og  <br/> Invitation til deling er oprettet  <br/> Du kan få flere oplysninger under [Brug overvågning af deling i overvågningsloggen](use-sharing-auditing.md).  |Delings- og adgangsanmodningsaktiviteter  |
    |Overfører eller downloader et dokument.  |Overført fil  <br/> Eller  <br/> Downloadet fil  |Fil- og mappeaktiviteter  |
    |Ændrer adgangstilladelserne til et websted.  |Ændrede webstedstilladelser  |Webstedsadministrationsaktiviteter  |

    I følgende tabel vises nogle almindelige mailrelaterede aktiviteter i Exchange Online.

    | Når en bruger gør dette... | Opret en besked for denne aktivitet | Aktivitetsgruppe |
    |:-----|:-----|:-----|
    |Sletter (fjerner) permanent en mail fra deres postkasse.  |Fjernede meddelelser fra postkasse  | Exchange postkasseaktiviteter  |
    |Sender en mail fra en delt postkasse.  |Sendt meddelelse med tilladelserne Send som  <br/> Og  <br/> Sendt meddelelse med tilladelsen Send på vegne  | Exchange postkasseaktiviteter  |

- Du kan også bruge Cmdlet'erne **New-ActivityAlert** og **Set-ActivityAlert** i Security & Compliance Center PowerShell til at oprette og redigere aktivitetsbeskeder. Vær opmærksom på følgende ting, hvis du bruger disse cmdlet'er til at oprette eller redigere aktivitetsbeskeder:

  - Hvis du bruger en cmdlet til at føje en aktivitet til den besked, der ikke er angivet på rullelisten **Aktiviteter** , vises der en meddelelse på egenskabssiden for beskeden med teksten "Denne besked indeholder brugerdefinerede handlinger, der ikke er angivet i vælgeren".

  - En god grund til at bruge cmdlet'erne til at oprette eller redigere en aktivitetsbesked er at sende mailmeddelelser til en person uden for din organisation. Denne eksterne bruger vises på listen over modtagere af beskeden. Men hvis du fjerner denne eksterne bruger fra beskeden, kan den pågældende bruger ikke føjes til beskeden igen ved hjælp af siden **Rediger besked** . Du skal tilføje den eksterne bruger igen ved hjælp af **Set-ActivityAlert-cmdlet'en** eller bruge Cmdlet'en **New-ActivityAlert** til at føje den samme (eller en anden) ekstern bruger til en ny besked.
