---
title: Administrer ventepositioner i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Få mere at vide om, hvordan du placerer ventepositioner på tilsynsførende og deres datakilder for at bevare relevant indhold til din eDiscovery-sag (Premium).
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: 16a4932993a652d8d7d71be78fd23a238fc90759
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939647"
---
# <a name="manage-holds-in-ediscovery-premium"></a>Administrer ventepositioner i eDiscovery (Premium)

Du kan bruge en Microsoft Purview eDiscovery-sag (Premium) til at oprette ventepositioner for at bevare indhold, der kan være relevant for din sag. Ved hjælp af funktionerne til eDiscovery-bevarelse (Premium) kan du placere ventepositioner på tilsynsførende og deres datakilder. Derudover kan du placere en ikke-frihedsberøvende venteposition på postkasser og OneDrive for Business websteder. Du kan også placere en venteposition på gruppepostkassen, SharePoint websted og OneDrive for Business websted for en Microsoft 365 gruppe. På samme måde kan du placere en venteposition på den postkasse og det websted, der er knyttet til Microsoft Teams. Når du placerer indholdsplaceringer i venteposition, opbevares indhold, indtil du frigiver vogteren, fjerner en bestemt dataplacering eller sletter politikken for bevarelse af data helt.

## <a name="manage-custodian-based-holds"></a>Administrer frihedsberøvende bevarelser

I nogle tilfælde kan du have et sæt tilsynsførende, som du har identificeret og har besluttet at bevare deres data i løbet af sagen. Når disse tilsynsførende sættes i venteposition i eDiscovery (Premium), føjes brugeren og deres valgte datakilder automatisk til en politik for frihedsberøvelse.

Sådan får du vist politikken for frihedsberøvelse:

1. På Microsoft Purview-overholdelsesportalen skal du klikke på **eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Gå til fanen **Kilder** for at tilføje vogtere i din sag. Hvis du vil vide mere om, hvordan du kan tilføje og placere tilsynsførende i en eDiscovery-sag (Premium), skal du se [Føj tilsynsførende til en sag](add-custodians-to-case.md). Hvis du allerede har tilføjet tilsynsførende og sat dem i venteposition, skal du gå til trin 3.

3. Gå til fanen **Ventepositioner,** og klik på **CustodianHold\<HoldId>**.

4. På pop op-siden kan du se statistik for venteposition for politikken. Du kan også udføre handlinger som f.eks. at anvende en forespørgsel på din frihedsberøvende venteposition. Du kan finde flere oplysninger om oprettelse af en ventepositionsforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Administrer ventepositioner uden frihedsberøvelse

Når du opretter en venteposition, har du følgende muligheder for at tilpasse omfanget af det indhold, der opbevares på de angivne indholdsplaceringer:

- Du opretter en uendelig venteposition, hvor alt indhold er sat i venteposition. Du kan også oprette en forespørgselsbaseret venteposition, hvor det kun er indhold, der svarer til en søgeforespørgsel, der sættes i venteposition.
  
- Du kan angive et datointerval, der kun indeholder det indhold, der blev sendt, modtaget eller oprettet inden for dette datointerval. Du kan også indeholde alt indhold, uanset hvornår det blev sendt, modtaget eller oprettet.

Sådan opretter du en eDiscovery-sag (Premium) uden frihedsberøvelse:

1. Klik på **eDiscovery > Avanceret** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> for at få vist listen over sager i din organisation.
  
2. Klik på **Åbn** ud for den sag, hvor ventepositionerne skal oprettes.
  
3. Klik på fanen **Ventepositioner** på startsiden for sagen.
  
4. Klik på **Opret** under fanen **Ventepositioner**.
  
5. På siden **Navngiv din venteposition** skal du give ventepositionen et navn. Navnet på ventepositionen skal være entydigt i din organisation.

6. (Valgfrit) Tilføj en beskrivelse af ventepositionen i feltet **Beskrivelse** .
  
7. Klik på **Næste**.
  
8. Vælg de indholdsplaceringer, du vil placere i venteposition. Du kan placere postkasser, websteder og offentlige mapper i venteposition.

   1. **Exchange mail** – Klik på **Vælg brugere, grupper eller teams,** og klik derefter på **Vælg brugere, grupper eller teams** igen for at angive, hvilke postkasser der skal placeres i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition på gruppemedlemmernes postkasser) til at placere dem i venteposition. Du kan også placere en venteposition på den tilknyttede postkasse for en Microsoft 365 gruppe eller et Microsoft-team. Markér afkrydsningsfeltet bruger, gruppe, team, klik på **Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > Når du klikker på **Vælg brugere, grupper eller teams** for at angive postkasser, der skal placeres i venteposition, er den postkassevælger, der vises, tom. Dette er tilsigtet for at forbedre ydeevnen. Hvis du vil føje personer til denne liste, skal du skrive et navn (mindst tre tegn) i søgefeltet.

   1. **SharePoint websteder** – Klik på **Vælg websteder,** og klik derefter på **Vælg websteder** igen for at angive, SharePoint og OneDrive for Business websteder, der skal placeres i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen for det SharePoint websted for en Microsoft 365 gruppe eller et Microsoft-team. Klik på **Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > URL-adressen til en brugers OneDrive-konto indeholder brugerens hovednavn (UPN) (f.eks. `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). I det sjældne tilfælde, at en persons UPN ændres, ændres vedkommendes OneDrive URL-adresse også for at inkorporere det nye UPN. Hvis en brugers OneDrive konto er en del af en ikke-frihedsberøvende venteposition, og brugerens UPN ændres, skal du opdatere ventepositionen og pege på den nye ONEDRIVE URL-adresse. Du kan få flere oplysninger under [Sådan påvirker UPN-ændringer OneDrive URL-adressen](/onedrive/upn-changes).

   1. **Exchange offentlige mapper** – Flyt til/fra-knappen til positionen Alle for at sætte alle offentlige mapper i din Exchange Online organisation i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-kontakten være angivet til **Ingen** , hvis du ikke vil sætte offentlige mapper i venteposition.

9. Når du er færdig med at føje indholdsplaceringer til ventepositionen, skal du klikke på **Næste**.
  
10. Hvis du vil oprette en forespørgselsbaseret venteposition med betingelser, skal du fuldføre følgende. Ellers skal du blot klikke på **Næste**.

    - I feltet under **Nøgleord** skal du skrive en søgeforespørgsel i feltet, så det kun er det indhold, der opfylder søgekriterierne, der sættes i venteposition. Du kan angive nøgleord, meddelelsesegenskaber eller dokumentegenskaber, f.eks. filnavne. Du kan også bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. AND, OR eller NOT. Hvis du lader nøgleordsfeltet være tomt, sættes alt indhold, der er placeret på de angivne indholdsplaceringer, i venteposition.

    - Klik på  **Tilføj** betingelser for at tilføje en eller flere betingelser for at indsnævre søgeforespørgslen for ventepositionen. Hver betingelse føjer en delsætning til den KQL-søgeforespørgsel, der oprettes og køres, når du opretter ventepositionen. Du kan f.eks. angive et datointerval, så mail- eller webstedsdokumenter, der blev oprettet inden for det datointerval, sættes i venteposition. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i nøgleordsfeltet) af operatoren AND. Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og den betingelse, der skal sættes i venteposition.

     Du kan finde flere oplysninger om oprettelse af en søgeforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Når du har konfigureret en forespørgselsbaseret venteposition, skal du klikke på **Næste**.

12. Gennemse dine indstillinger, og klik derefter på **Opret denne venteposition**.

> [!NOTE]
> Når du opretter en forespørgselsbaseret venteposition, sættes alt indhold fra valgte placeringer i første omgang i venteposition. Efterfølgende ryddes alt indhold, der ikke stemmer overens med den angivne forespørgsel, fra ventepositionen hver 7. til 14. dag. En forespørgselsbaseret venteposition rydder dog ikke indhold, hvis der anvendes mere end fem ventepositioner af nogen type på en indholdsplacering, eller hvis et element har problemer med indeksering.

> [!NOTE]
> Hvis SMTP-adressen for brugeren ændres, når du har sat brugerens postkasse i venteposition, forbliver postkassen i venteposition. Hvis du vil bruge den nye SMTP-adresse til at placere venteposition, skal du oprette en ny venteposition.

## <a name="view-hold-statistics"></a>Vis statistik for venteposition

Efter et stykke tid vises oplysninger om den nye venteposition i detaljeruden under fanen **Ventepositioner** for den valgte venteposition. Disse oplysninger omfatter antallet af postkasser og websteder, der er i venteposition, og statistik over det indhold, der blev sat i venteposition, f.eks. det samlede antal elementer og størrelsen af elementer, der er sat i venteposition, og den sidste gang statistik for venteposition blev beregnet. Disse statistikoplysninger hjælper dig med at identificere, hvor meget indhold der er relateret til eDiscovery-sagen.

Vær opmærksom på følgende ting i forbindelse med statistik for venteposition:

- Det samlede antal elementer i venteposition angiver antallet af elementer fra alle indholdskilder, der er sat i venteposition. Hvis du har oprettet en forespørgselsbaseret venteposition, angiver denne statistik antallet af elementer, der svarer til forespørgslen.
  
- Antallet af elementer i venteposition omfatter også ikke-indekserede elementer, der findes på indholdsplaceringerne. Hvis du opretter en forespørgselsbaseret venteposition, sættes alle ikke-indekserede elementer på indholdsplaceringerne i venteposition. Dette omfatter ikke-indekserede elementer, der ikke svarer til søgekriterierne for en forespørgselsbaseret venteposition og ikke-indekserede elementer, der kan falde uden for en datoområdebetingelse. Dette er forskelligt fra det, der sker, når du kører en indholdssøgning, hvor ikke-indekserede elementer, der ikke stemmer overens med søgeforespørgslen eller udelades af en datoområdebetingelse, ikke er inkluderet i søgeresultaterne. Du kan finde flere oplysninger om ikke-indekserede elementer [under Delvist indekserede elementer i indholdssøgning i Office 365](partially-indexed-items-in-content-search.md).

- Du kan få den seneste statistik for venteposition ved at klikke på Opdater statistik for at køre et søgeestimat, der beregner det aktuelle antal elementer i venteposition.

- Hvis det er nødvendigt, skal du klikke på Opdater på værktøjslinjen for at opdatere statistik for venteposition i detaljeruden.

- Det er normalt, at antallet af elementer i venteposition øges over tid, fordi brugere, hvis postkasse eller websted er i venteposition, normalt sender eller modtager en ny mail og opretter nye SharePoint og OneDrive for Business dokumenter.

- Hvis et SharePoint websted eller en OneDrive konto flyttes til et andet område i et multi-geo-miljø, medtages statistikkerne for det pågældende websted ikke i statistik for venteposition. Indholdet på webstedet er dog stadig i venteposition. Hvis et websted flyttes til et andet område, opdateres den URL-adresse, der vises i ventepositionen, heller ikke. Du skal redigere ventepositionen og opdatere URL-adressen.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Sæt Microsoft Teams og Office 365 grupper i venteposition

Microsoft Teams er baseret på Office 365 Grupper. Derfor er det det samme at sætte dem i venteposition i eDiscovery (Premium).

- **Hvordan gør jeg kort en ekstra Microsoft 365-grupper eller Microsoft Teams site til en tilsynsførende? Hvad med at tilbageholde Microsoft 365-grupper og Microsoft Teams?** Microsoft Teams er bygget på Microsoft 365-grupper. Derfor er det det samme at sætte dem i venteposition i en eDiscovery-sag. Vær opmærksom på følgende ting, når du placerer Microsoft 365-grupper og Microsoft Teams i venteposition.

  - Hvis du vil placere indhold i Microsoft 365-grupper og Microsoft Teams i venteposition, skal du angive postkassen og SharePoint websted, der er knyttet til en gruppe eller et team.
  
  - Kør **Get-UnifiedGroup-cmdlet'en** i Exchange Online for at få vist egenskaber for en Microsoft 365 gruppe eller Et Microsoft-team. Dette er en god måde at få URL-adressen til det websted, der er knyttet til en Microsoft 365 gruppe eller et Microsoft-team. Følgende kommando viser f.eks. de valgte egenskaber for en Microsoft 365 gruppe med navnet Senior Leadership Team:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Hvis du vil køre den Get-UnifiedGroup cmdlet, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har fået tildelt rollen View-Only Modtagere.

  - Når der søges i en brugers postkasse, bliver der ikke søgt i Microsoft 365 gruppe eller Microsoft Team, som brugeren er medlem af. På samme måde er det kun gruppepostkassen og gruppewebstedet, der sættes i venteposition, når du placerer en Microsoft 365 gruppe- eller Microsoft Team-venteposition. Postkasserne og OneDrive for Business websteder for gruppemedlemmer sættes ikke i venteposition, medmindre du udtrykkeligt tilføjer dem som vogtere eller placerer deres datakilder i venteposition. Hvis du derfor har brug for at placere en Microsoft 365 gruppe eller Microsoft-team i venteposition for en bestemt tilsynsførende, kan du overveje at knytte gruppewebstedet og gruppepostkassen til vogteren (se Administration af tilsynsførende i eDiscovery (Premium)). Hvis Microsoft 365-gruppen eller Microsoft-teamet ikke kan henføres til en enkelt tilsynsførende, kan du overveje at føje kilden til en ikke-frihedsberøvende venteposition.
  - Hvis du vil hente en liste over medlemmerne af en Microsoft 365-gruppe eller Microsoft Team, kan du få vist egenskaberne på siden [**HomeGroups**](https://go.microsoft.com/fwlink/p/?linkid=2052855)  >  i Microsoft 365 Administration. Du kan også køre følgende kommando i Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Hvis du vil køre cmdlet'en **Get-UnifiedGroupLinks**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har tildelt rollen View-Only modtagere.

  - Kanalsamtaler, der er en del af en Microsoft Teams kanal, gemmes i den postkasse, der er knyttet til teamet. På samme måde gemmes filer, som teammedlemmer deler i en kanal, på teamets SharePoint websted. Derfor skal du placere Microsoft Team-postkassen og SharePoint websted i venteposition for at bevare samtaler og filer i en kanal.
  
  - Alternativt gemmes samtaler, der er en del af chatlisten i Microsoft Teams i postkassen for den bruger, der deltager i chatten.  Filer, som en bruger deler i Chat-samtaler, gemmes på OneDrive for Business websted for den bruger, der deler filen. Derfor skal du placere de enkelte brugerpostkasser og OneDrive for Business websteder i venteposition for at bevare samtaler og filer på chatlisten.
  
  - Alle Microsoft Team- eller teamkanaler indeholder en wiki til notetagning og samarbejde. Wikiindholdet gemmes automatisk i en fil med et .mht-format. Denne fil er gemt i dokumentbiblioteket Teams wikidata på teamets SharePoint websted. Du kan sætte indholdet i wikien i venteposition ved at sætte teamets SharePoint websted i venteposition.

    > [!NOTE]
    > Muligheden for at bevare wikiindhold for en Microsoft Team- eller teamkanal (når du placerer teamets SharePoint websted i venteposition) blev udgivet den 22. juni 2017. Hvis et teamwebsted er i venteposition, bevares wikiindholdet fra den pågældende dato. Men hvis et teamwebsted er i venteposition, og wikiindholdet blev slettet før den 22. juni 2017, blev wikiindholdet ikke bevaret.
