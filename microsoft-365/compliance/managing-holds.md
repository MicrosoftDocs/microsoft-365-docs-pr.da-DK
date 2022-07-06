---
title: Administrer ventepositioner i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/27/2022
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
description: Få mere at vide om, hvordan du placerer ventepositioner på tilsynsførende og deres datakilder for at bevare relevant indhold i din eDiscovery-sag (Premium).
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: f7c47afe74c4d48036160d0fbb0c9717f884bc46
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629437"
---
# <a name="manage-holds-in-ediscovery-premium"></a>Administrer ventepositioner i eDiscovery (Premium)

Du kan bruge en Microsoft Purview eDiscovery (Premium)-sag til at oprette ventepositioner for at bevare indhold, der kan være relevant for din sag. Ved hjælp af funktionerne til eDiscovery -bevarelse (Premium) kan du placere ventepositioner på tilsynsførende og deres datakilder. Derudover kan du placere en ikke-frihedsberøvende venteposition på postkasser og OneDrive for Business websteder. Du kan også placere en venteposition på gruppepostkassen, SharePoint-webstedet og OneDrive for Business websted for en Microsoft 365-gruppe. På samme måde kan du placere en venteposition på den postkasse og det websted, der er knyttet til Microsoft Teams. Når du placerer indholdsplaceringer i venteposition, opbevares indhold, indtil du frigiver vogteren, fjerner en bestemt dataplacering eller sletter politikken for bevarelse af data helt.

## <a name="manage-custodian-based-holds"></a>Administrer frihedsberøvende bevarelser

I nogle tilfælde kan du have et sæt tilsynsførende, som du har identificeret og har besluttet at bevare deres data i løbet af sagen. Når disse tilsynsførende sættes i venteposition i eDiscovery (Premium), føjes brugeren og deres valgte datakilder automatisk til en politik om frihedsberøvelse.

Sådan får du vist politikken for frihedsberøvelse:

1. I Microsoft Purview-compliance-portal skal du klikke på **eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Gå til fanen **Kilder** for at tilføje vogtere i din sag. Hvis du vil vide mere om, hvordan du kan tilføje og placere tilsynsførende i venteposition i en eDiscovery-sag (Premium), skal du se [Føj tilsynsførende til en sag](add-custodians-to-case.md). Hvis du allerede har tilføjet tilsynsførende og sat dem i venteposition, skal du gå til trin 3.

3. Gå til fanen **Ventepositioner,** og klik på **CustodianHold\<HoldId>**.

4. På pop op-siden kan du udføre handlinger som f.eks. at anvende en forespørgsel på din frihedsberøvende venteposition. Du kan finde flere oplysninger om oprettelse af en ventepositionsforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Administrer ventepositioner uden frihedsberøvelse

Når du opretter en venteposition, har du følgende muligheder for at tilpasse omfanget af det indhold, der opbevares på de angivne indholdsplaceringer:

- Du opretter en uendelig venteposition, hvor alt indhold er sat i venteposition. Du kan også oprette en forespørgselsbaseret venteposition, hvor det kun er indhold, der svarer til en søgeforespørgsel, der sættes i venteposition.
  
- Du kan angive et datointerval, der kun indeholder det indhold, der blev sendt, modtaget eller oprettet inden for dette datointerval. Du kan også indeholde alt indhold, uanset hvornår det blev sendt, modtaget eller oprettet.

Sådan opretter du en ikke-frihedsberøvende venteposition for en eDiscovery-sag (Premium):

1. Klik på **eDiscovery > Avanceret** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> for at få vist listen over sager i din organisation.
  
2. Klik på **Åbn** ud for den sag, hvor ventepositionerne skal oprettes.
  
3. Klik på fanen **Ventepositioner** på startsiden for sagen.
  
4. Klik på **Opret** under fanen **Ventepositioner**.
  
5. På siden **Navngiv din venteposition** skal du give ventepositionen et navn. Navnet på ventepositionen skal være entydigt i din organisation.

6. (Valgfrit) Tilføj en beskrivelse af ventepositionen i feltet **Beskrivelse** .
  
7. Klik på **Næste**.
  
8. Vælg de indholdsplaceringer, du vil placere i venteposition. Du kan placere postkasser, websteder og offentlige mapper i venteposition.

   1. **Exchange-mail** – Klik på **Vælg brugere, grupper eller teams,** og klik derefter på **Vælg brugere, grupper eller teams** igen for at angive, at postkasser skal placeres i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition på gruppemedlemmernes postkasser) til at placere dem i venteposition. Du kan også placere en venteposition på den tilknyttede postkasse for en Microsoft 365-gruppe eller et Microsoft-team. Markér afkrydsningsfeltet bruger, gruppe, team, klik på **Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > Når du klikker på **Vælg brugere, grupper eller teams** for at angive postkasser, der skal placeres i venteposition, er den postkassevælger, der vises, tom. Dette er tilsigtet for at forbedre ydeevnen. Hvis du vil føje personer til denne liste, skal du skrive et navn (mindst tre tegn) i søgefeltet.

   1. **SharePoint-websteder** – Klik på **Vælg websteder,** og klik derefter på **Vælg websteder** igen for at angive SharePoint og OneDrive for Business websteder, der skal placeres i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til SharePoint-webstedet for en Microsoft 365-gruppe eller et Microsoft-team. Klik på **Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > URL-adressen til en brugers OneDrive-konto indeholder brugerens hovednavn (UPN) (f.eks. `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). I det sjældne tilfælde, at en persons UPN ændres, ændres vedkommendes URL-adresse til OneDrive også for at inkorporere det nye UPN. Hvis en brugers OneDrive-konto er en del af en ikke-frihedsberøvende venteposition, og brugerens UPN ændres, skal du opdatere ventepositionen og pege på den nye URL-adresse til OneDrive. Du kan få flere oplysninger under [Sådan påvirker UPN-ændringer URL-adressen til OneDrive](/onedrive/upn-changes).

   1. **Offentlige Exchange-mapper** – Flyt til/fra-skift til positionen Alle for at sætte alle offentlige mapper i din Exchange Online organisation i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-kontakten være angivet til **Ingen** , hvis du ikke vil sætte offentlige mapper i venteposition.

9. Når du er færdig med at føje indholdsplaceringer til ventepositionen, skal du klikke på **Næste**.
  
10. Hvis du vil oprette en forespørgselsbaseret venteposition med betingelser, skal du fuldføre følgende. Ellers skal du blot klikke på **Næste**.

    - I feltet under **Nøgleord** skal du skrive en søgeforespørgsel i feltet, så det kun er det indhold, der opfylder søgekriterierne, der sættes i venteposition. Du kan angive nøgleord, meddelelsesegenskaber eller dokumentegenskaber, f.eks. filnavne. Du kan også bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. AND, OR eller NOT. Hvis du lader nøgleordsfeltet være tomt, sættes alt indhold, der er placeret på de angivne indholdsplaceringer, i venteposition.

    - Klik på  **Tilføj** betingelser for at tilføje en eller flere betingelser for at indsnævre søgeforespørgslen for ventepositionen. Hver betingelse føjer en delsætning til den KQL-søgeforespørgsel, der oprettes og køres, når du opretter ventepositionen. Du kan f.eks. angive et datointerval, så mail- eller webstedsdokumenter, der blev oprettet inden for det datointerval, sættes i venteposition. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i nøgleordsfeltet) af operatoren AND. Det betyder, at elementer skal opfylde både nøgleordsforespørgslen og den betingelse, der skal sættes i venteposition.

     Du kan finde flere oplysninger om oprettelse af en søgeforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Når du har konfigureret en forespørgselsbaseret venteposition, skal du klikke på **Næste**.

12. Gennemse dine indstillinger, og klik derefter på **Opret denne venteposition**.

> [!NOTE]
> Når du opretter en forespørgselsbaseret venteposition, sættes alt indhold fra valgte placeringer i første omgang i venteposition. Når timerjobbet i enten Exchange eller SharePoint kører, ryddes alt indhold, der ikke stemmer overens med den angivne forespørgsel, fra ventepositionen. Når antallet af tegn på tværs af alle forespørgsler på en enkelt placering overstiger 10.000 tegn, sættes hele placeringen i venteposition. 

> [!NOTE]
> Hvis SMTP-adressen for brugeren ændres, når du har sat brugerens postkasse i venteposition, forbliver postkassen i venteposition. Hvis du vil bruge den nye SMTP-adresse til at placere venteposition, skal du oprette en ny venteposition.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Sæt microsoft Teams og Office 365 grupper i venteposition

Microsoft Teams er baseret på Office 365 grupper. Derfor er det det samme at sætte dem i venteposition i eDiscovery (Premium).

- **Hvordan gør jeg du knytte et ekstra Microsoft 365-grupper- eller Microsoft Teams-websted til en tilsynsførende? Og hvad med at sætte en ikke-frihedsberøvende venteposition på Microsoft 365-grupper og Microsoft Teams?** Microsoft Teams er baseret på Microsoft 365-grupper. Derfor er det det samme at sætte dem i venteposition i en eDiscovery-sag. Vær opmærksom på følgende ting, når Microsoft 365-grupper og Microsoft Teams sættes i venteposition.

  - Hvis du vil placere indhold i venteposition i Microsoft 365-grupper og Microsoft Teams, skal du angive den postkasse og det SharePoint-websted, der er knyttet til en gruppe eller et team.
  
  - Kør **Get-UnifiedGroup-cmdlet'en** i Exchange Online for at få vist egenskaber for en Microsoft 365-gruppe eller et Microsoft-team. Dette er en god måde at få URL-adressen til det websted, der er knyttet til en Microsoft 365-gruppe eller et Microsoft-team. Følgende kommando viser f.eks. de valgte egenskaber for en Microsoft 365-gruppe med navnet Senior Leadership Team:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > Hvis du vil køre den Get-UnifiedGroup cmdlet, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har fået tildelt rollen View-Only Modtagere.

  - Når der søges i en brugers postkasse, bliver der ikke søgt i microsoft 365-grupper eller Microsoft-team, som brugeren er medlem af. Når du placerer en Microsoft 365-gruppe eller Microsoft Team-venteposition, er det på samme måde kun gruppepostkassen og gruppewebstedet, der sættes i venteposition. postkasserne og OneDrive for Business websteder for gruppemedlemmer sættes ikke i venteposition, medmindre du udtrykkeligt tilføjer dem som vogtere eller placerer deres datakilder i venteposition. Hvis du derfor har brug for at placere en Microsoft 365-gruppe eller Microsoft-gruppe i venteposition for en bestemt tilsynsførende, kan du overveje at knytte gruppewebstedet og gruppepostkassen til vogteren (se Administration af tilsynsførende i eDiscovery (Premium)). Hvis Microsoft 365-gruppen eller Microsoft-teamet ikke kan tilskrives en enkelt tilsynsførende, kan du overveje at føje kilden til en bevarelse uden frihedsberøvelse.
  - Hvis du vil hente en liste over medlemmerne af en Microsoft 365-gruppe eller Et Microsoft-team, kan du få vist egenskaberne på siden **Hjemmegrupper** >  i Microsoft 365 Administration.[](https://go.microsoft.com/fwlink/p/?linkid=2052855) Du kan også køre følgende kommando i Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > Hvis du vil køre cmdlet'en **Get-UnifiedGroupLinks**, skal du have tildelt rollen View-Only modtagere i Exchange Online eller være medlem af en rollegruppe, der har tildelt rollen View-Only modtagere.

  - Kanalsamtaler, der er en del af en Microsoft Teams-kanal, gemmes i den postkasse, der er knyttet til teamet. På samme måde gemmes filer, som teammedlemmer deler i en kanal, på teamets SharePoint-websted. Derfor skal du placere Microsoft Team-postkassen og SharePoint-webstedet i venteposition for at bevare samtaler og filer i en kanal.
  
  - Alternativt gemmes samtaler, der er en del af chatlisten i Microsoft Teams, i postkassen for den bruger, der deltager i chatten.  Filer, som en bruger deler i Chat-samtaler, gemmes på OneDrive for Business websted for den bruger, der deler filen. Derfor skal du placere de enkelte brugerpostkasser og OneDrive for Business websteder i venteposition for at bevare samtaler og filer på chatlisten.
  
  - Alle Microsoft Team- eller teamkanaler indeholder en wiki til notetagning og samarbejde. Wikiindholdet gemmes automatisk i en fil med et .mht-format. Denne fil er gemt i Teams Wikidata-dokumentbiblioteket på teamets SharePoint-websted. Du kan sætte indholdet i wikien i venteposition ved at sætte teamets SharePoint-websted i venteposition.

    > [!NOTE]
    > Muligheden for at bevare wikiindhold for en Microsoft Team- eller teamkanal (når du placerer teamets SharePoint-websted i venteposition) blev udgivet den 22. juni 2017. Hvis et teamwebsted er i venteposition, bevares wikiindholdet fra den pågældende dato. Men hvis et teamwebsted er i venteposition, og wikiindholdet blev slettet før den 22. juni 2017, blev wikiindholdet ikke bevaret.
