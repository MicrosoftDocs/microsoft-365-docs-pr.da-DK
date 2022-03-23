---
title: Administrer ventende Advanced eDiscovery
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
description: Få mere at vide om, hvordan du anbringer ventende dokumenter for hjælpeere og deres datakilder for at bevare relevant indhold Advanced eDiscovery din sag.
ms.custom:
- seo-marvel-mar2020
- admindeeplinkMAC
ms.openlocfilehash: d731c0cda31f96f5274ca0c2fd56d5e14901f3a9
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63587714"
---
# <a name="manage-holds-in-advanced-ediscovery"></a>Administrer ventende Advanced eDiscovery

Du kan bruge en Advanced eDiscovery til at oprette ventende dokumenter for at bevare indhold, der kan være relevant for din sag. Ved hjælp Advanced eDiscovery funktioner til venteposition kan du placere ventepositioner for hjælpeianere og deres datakilder. Desuden kan du placere et ventepositions hold på postkasser og OneDrive for Business websteder. Du kan også placere en venteposition på gruppens postkasse, SharePoint websted og OneDrive for Business til en Microsoft 365 gruppe. På samme måde kan du placere en venteposition på den postkasse og det websted, der er knyttet Microsoft Teams. Når du placerer indholdsplaceringer i venteposition, opbevares indhold, indtil du frigiver det sted, hvor du er, kan du fjerne en bestemt dataplacering eller helt slette politikken for venteposition.

## <a name="manage-custodian-based-holds"></a>Administrer forevaringsbaserede vente hold

I nogle tilfælde kan du have en række af ydsere, som du har identificeret og har besluttet at bevare deres data i løbet af sagen. Når disse Advanced eDiscovery er sat i venteposition, føjes brugeren og deres valgte datakilder automatisk til en politik for opbevaring af brugere.

Sådan får du vist politikken for fremvisere, der er i venteposition:

1. I Microsoft 365 Overholdelsescenter skal du klikke **på eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Gå til fanen Kilder **for** at tilføje y-y-2-4 i din sag. Du kan få mere at vide om, hvordan du kan tilføje og placere y-2016-førere i venteposition i en Advanced eDiscovery tilfælde ved at se Føj [ydsere til en sag](add-custodians-to-case.md). Hvis du allerede har tilføjet hjælpeere og sat dem i venteposition, skal du gå til trin 3.

3. Gå til fanen **Ventende,** og klik **på ØverianHold\<HoldId>**.

4. På pop op-siden kan du se holdstatistik for politikken. Du kan også udføre handlinger som f.eks. at anvende en forespørgsel på din forespørgselsbaseret venteposition. Du kan finde flere oplysninger om oprettelse af en ventepositionsforespørgsel og brug af betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

## <a name="manage-non-custodial-holds"></a>Administrere vente hold, der ikke er ledende

Når du opretter en venteposition, har du følgende muligheder for at begrænse det indhold, der opbevares på de angivne indholdsplaceringer:

- Du opretter en uendelig venteposition, hvor alt indhold er sat i venteposition. Du kan også oprette en forespørgselsbaseret venteposition, hvor kun indhold, der svarer til en søgeforespørgsel, er sat i venteposition.
  
- Du kan angive et datointerval, der kun skal indeholde det indhold, der blev sendt, modtaget eller oprettet inden for det pågældende datointerval. Du kan også opbevare alt indhold, uanset hvornår det blev sendt, modtaget eller oprettet.

Sådan oprettes et venteposition for en Advanced eDiscovery en sag:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter skal</a> du klikke **på eDiscovery > Avanceret** for at få vist listen over sager i din organisation.
  
2. Klik **på** Åbn ud for den sag, hvor du vil oprette ventende filer.
  
3. Klik på fanen Vente hold på **startsiden** for sagen.
  
4. Klik på **Opret** under fanen Vente **hold**.
  
5. Giv **ventepositionen et** navn på siden Navngive din venteposition. Navnet på ventepositionen skal være entydigt i organisationen.

6. (Valgfrit) Tilføj en **beskrivelse** af ventepositionen i feltet Beskrivelse.
  
7. Klik på **Næste**.
  
8. Vælg de indholdsplaceringer, du vil placere i venteposition. Du kan placere postkasser, websteder og offentlige mapper i venteposition.

   1. **Exchange -** Klik på Vælg brugere, grupper eller **teams,** og klik derefter på Vælg brugere **,** grupper eller teams igen for at angive postkasser, der skal være i venteposition. Brug søgefeltet til at finde brugerpostkasser og distributionsgrupper (til at placere en venteposition i gruppemedlemmers postkasser) for at placere dem i venteposition. Du kan også placere en venteposition i den tilknyttede postkasse for Microsoft 365 gruppe eller et Microsoft Team. Markér afkrydsningsfeltet bruger, gruppe, team, klik på **Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > Når du klikker **på Vælg brugere, grupper eller teams** for at angive postkasser, der skal være i venteposition, er den viste postkassevælger tom. Dette er med henblik på at forbedre ydeevnen. Hvis du vil føje personer til denne liste, skal du skrive et navn (minimum 3 tegn) i søgefeltet.

   1. **SharePoint websteder –** Klik på Vælg websteder, og klik derefter på  Vælg websteder igen for at SharePoint og OneDrive for Business websteder, der skal anbringes i venteposition. Skriv URL-adressen for hvert websted, du vil placere i venteposition. Du kan også tilføje URL-adressen til SharePoint for en Microsoft 365 gruppe eller et Microsoft Team. Klik **på Vælg**, og klik derefter på **Udført**.

      > [!NOTE]
      > URL-adressen til en brugers konto OneDrive brugerens hovednavn (UPN) (f.eks. `https://alpinehouse-my.sharepoint.com/personal/sarad_alpinehouse_onmicrosoft_com`). Hvis det sjældent er tilfældet, at en persons UPN ændres, ændres personens URL-OneDrive til at inkorporere det nye UPN. Hvis en brugers OneDrive-konto er en del af et ikke-sikkerhedsbaseret venteposition, og brugerens UPN ændres, skal du opdatere ventepositionen og pege på den nye OneDrive URL-adresse. Du kan finde flere oplysninger [under Sådan påvirker UPN OneDrive URL-adressen](/onedrive/upn-changes).

   1. **Exchange offentlige mapper** – Flyt til/fra-knappen til positionen Alle for at sætte alle offentlige mapper i din Exchange Online i venteposition. Du kan ikke vælge bestemte offentlige mapper, der skal sættes i venteposition. Lad til/fra-knappen være **indstillet til** Ingen, hvis du ikke vil sætte offentlige mapper i venteposition.

9. Når du er færdig med at føje indholdsplaceringer til ventepositionen, skal du klikke på **Næste**.
  
10. Hvis du vil oprette en forespørgselsbaseret venteposition med betingelser, skal du fuldføre følgende. Ellers skal du bare klikke **på Næste**.

    - I feltet under Nøgleord **skal du** skrive en søgeforespørgsel i feltet, så kun det indhold, der opfylder søgekriterierne, er sat i venteposition. Du kan angive nøgleord, meddelelsesegenskaber eller dokumentegenskaber, f.eks. filnavne. Du kan også bruge mere komplekse forespørgsler, der bruger en boolesk operator, f.eks. OG, ELLER eller IKKE. Hvis du lader feltet nøgleord være tomt, vil alt indhold, der er placeret på de angivne indholdsplaceringer, være sat i venteposition.

    - Klik  **på Tilføj** betingelser for at tilføje en eller flere betingelser for at indsnævre søgeforespørgslen om venteposition. Hver betingelse føjer en delsætning til KQL-søgeforespørgslen, der oprettes og køres, når du opretter ventepositionen. Du kan f.eks. angive et datointerval, så mails eller webstedsdokumenter, der er oprettet inden for datointervallet, er sat i venteposition. En betingelse er logisk forbundet med nøgleordsforespørgslen (angivet i feltet nøgleord) af operatoren AND. Det betyder, at elementerne skal opfylde både nøgleordsforespørgslen og betingelsen, der skal være sat i venteposition.

     Du kan finde flere oplysninger om at oprette en søgeforespørgsel og bruge betingelser under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](/office365/SecurityCompliance/keyword-queries-and-search-conditions).

11. Når du har konfigureret en forespørgselsbaseret venteposition, skal du klikke **på Næste**.

12. Gennemse dine indstillinger, og klik derefter på **Opret denne venteposition**.

> [!NOTE]
> Når du opretter en forespørgselsbaseret venteposition, sættes alt indhold fra valgte placeringer i venteposition. Efterfølgende fjernes alt indhold, der ikke stemmer overens med den angivne forespørgsel, fra ventepositionen hver syv til 14 dage. Men forespørgselsbaseret venteposition rydder ikke indhold, hvis der anvendes mere end fem ventepositioner af enhver type på en indholdsplacering, eller hvis et element har indekseringsproblemer.

> [!NOTE]
> Hvis BRUGERENS SMTP-adresse ændres, når du har sæt brugerens postkasse i venteposition, forbliver postkassen i venteposition. Hvis du vil bruge den nye SMTP-adresse til at placere venteposition, skal du oprette en ny venteposition.

## <a name="view-hold-statistics"></a>Få vist holdstatistik

Efter et stykke tid vises der oplysninger om den nye venteposition i detaljeruden på fanen **Venteposition** for den valgte venteposition. Disse oplysninger omfatter antallet af postkasser og websteder i venteposition og statistik om det indhold, der blev sat i venteposition, f.eks. det samlede antal og størrelsen af elementer, der er sat i venteposition, og den seneste gang statistik for venteposition blev beregnet. Disse holdstatistik hjælper dig med at identificere, hvor meget indhold der er relateret til eDiscovery-sagen.

Husk følgende i forbindelse med statistik for ventepositioner:

- Det samlede antal elementer, der er sat i venteposition, angiver antallet af elementer fra alle indholdskilder, der er sat i venteposition. Hvis du har oprettet en forespørgselsbaseret venteposition, angiver denne statistik antallet af elementer, der svarer til forespørgslen.
  
- Antallet af elementer, der er i venteposition, omfatter også uindsiderede elementer, der findes på indholdsplaceringerne. Hvis du opretter en forespørgselsbaseret venteposition, er alle elementer, der ikke er identificeret på indholdsplaceringerne, sat i venteposition. Dette omfatter ikke-opdaterede elementer, der ikke opfylder søgekriterierne for forespørgselsbaserede ventepositioner og ikke-opdaterede elementer, der kan falde uden for en betingelse for datointervallet. Dette er anderledes end det, der sker, når du kører en indholdssøgning, hvor uindsøgede elementer, der ikke svarer til søgeforespørgslen eller udelades af en betingelse for datointerval, ikke medtages i søgeresultaterne. Du kan finde flere oplysninger om indekserede elementer i [Delvist indekserede elementer i Indholdssøgning Office 365](partially-indexed-items-in-content-search.md).

- Du kan få de seneste ventepositionsstatistik ved at klikke på Opdater statistik for at køre et søgeestimat, der beregner det aktuelle antal elementer i venteposition.

- Hvis det er nødvendigt, skal du klikke på Opdater på værktøjslinjen for at opdatere statistik for venteposition i detaljeruden.

- Det er normalt, at antallet af elementer, der er i venteposition, øges med tiden, fordi brugere, hvis postkasse eller websted er i venteposition, typisk sender eller modtager nye mails og opretter nye SharePoint og OneDrive for Business dokumenter.

- Hvis en SharePoint-websteds- eller OneDrive-konto flyttes til et andet område i et multi-geo-miljø, medtages statistikken for det pågældende websted ikke i ventepositionsstatistikken. Indholdet på webstedet er dog stadig i venteposition. Hvis et websted flyttes til et andet område, opdateres URL-adressen, der vises i venteposition, ikke. Du skal redigere ventepositionen og opdatere URL-adressen.

## <a name="place-a-hold-on-microsoft-teams-and-office-365-groups"></a>Sæt en venteposition på Microsoft Teams og Office 365 Grupper

Microsoft Teams er bygget på Office 365 Grupper. Derfor er det at placere dem i venteposition Advanced eDiscovery lignende.

- **Hvordan tilknytter jeg en ekstra Microsoft 365 gruppe eller et Microsoft Teams til en seer? Og hvad med at sætte en venteposition, der ikke er til Microsoft 365, på grupper Microsoft Teams?** Microsoft Teams er bygget på Microsoft 365 Grupper. Derfor er det at sætte dem i venteposition i en eDiscovery-sag på lignende måde. Vær opmærksom på følgende, når du placerer Microsoft 365 Grupper og Microsoft Teams i venteposition.

  - Hvis du vil placere indhold i Microsoft 365 Grupper og Microsoft Teams i venteposition, skal du angive den postkasse og det SharePoint websted, der er knyttet til en gruppe eller et team.
  
  - Kør **cmdlet'en Get-UnifiedGroup** i Exchange Online for at få vist egenskaber for Microsoft 365 eller Microsoft Team. Dette er en god måde at hente URL-adressen til det websted, der er knyttet til en Microsoft 365-gruppe eller et Microsoft-team. Eksempelvis viser følgende kommando de valgte egenskaber for en gruppe Microsoft 365 seniorledelse:

    ```console
    Get-UnifiedGroup "Senior Leadership Team" | FL DisplayName,Alias,PrimarySmtpAddress,SharePointSiteUrl
    DisplayName            : Senior Leadership Team
    Alias                  : seniorleadershipteam
    PrimarySmtpAddress     : seniorleadershipteam@contoso.onmicrosoft.com
    SharePointSiteUrl      : https://contoso.sharepoint.com/sites/seniorleadershipteam
    ```

    > [!NOTE]
    > For at køre cmdlet'en Get-UnifiedGroup skal du være tildelt rollen View-Only-modtagere i Exchange Online eller være medlem af en rollegruppe, der har fået tildelt rollen View-Only Modtagere.

  - Når der søges i en brugers postkasse, søges der ikke i Microsoft 365 gruppe eller Microsoft-team, som brugeren er medlem af. På samme måde gælder det, at når du placerer en Microsoft 365-gruppe eller et Microsoft-team i venteposition, er det kun gruppepostkassen og gruppewebstedet, der er sat i venteposition. Postkasser og OneDrive for Business-websteder for gruppemedlemmer sættes ikke i venteposition, medmindre du eksplicit tilføjer dem som brugere eller placerer deres datakilder i venteposition. Hvis du har brug for at placere en Microsoft 365-gruppe eller Microsoft-team i venteposition for en bestemt afhængig bruger, bør du overveje at knytte gruppewebstedet og gruppepostkassen til den personalechef, du vil administrere Advanced eDiscovery). Hvis gruppen Microsoft 365 Microsoft-teamet ikke kan tilgives en enkelt leder, kan du overveje at føje kilden til et venteposition, der ikke er tilhold.
  - Hvis du vil have en liste over medlemmer af en Microsoft 365-gruppe eller Microsoft-team,  >  kan du få vist egenskaberne på siden Hjemmegrupper på Microsoft 365 Administration.[](https://go.microsoft.com/fwlink/p/?linkid=2052855) Alternativt kan du køre følgende kommando i Exchange Online PowerShell:

    ```powershell
    Get-UnifiedGroupLinks <group or team name> -LinkType Members | FL DisplayName,PrimarySmtpAddress
    ```

    > [!NOTE]
    > For at køre cmdlet'en **Get-UnifiedGroupLinks** skal du være tildelt rollen View-Only-modtagere i Exchange Online eller være medlem af en rollegruppe, der er tildelt rollen View-Only Modtagere.

  - Kanalsamtaler, der er en del af Microsoft Teams kanal, gemmes i den postkasse, der er knyttet til teamet. Ligeledes gemmes filer, som teammedlemmer deler i en kanal, på teamets websted SharePoint webstedet. Derfor skal du placere Microsoft-teampostkassen og SharePoint i venteposition for at bevare samtaler og filer i en kanal.
  
  - Alternativt gemmes samtaler, der er en del af chatlisten i Microsoft Teams, i postkassen for de brugere, der deltager i chatten.  Filer, som en bruger deler i chatsamtaler, gemmes på OneDrive for Business for den bruger, der deler filen. Derfor skal du placere de enkelte brugerpostkasser og OneDrive for Business i venteposition for at bevare samtaler og filer på chatlisten.
  
  - Alle Microsoft-teams eller teamkanaler indeholder en wiki til notetagning og samarbejde. Wiki-indholdet gemmes automatisk i en fil med .mht-format. Denne fil er gemt i Teams wikidatadokumentbiblioteket på teamets websted SharePoint websted. Du kan sætte indholdet i wikien i venteposition ved at placere teamets websted SharePoint i venteposition.

    > [!NOTE]
    > Muligheden for at bevare Wiki-indhold til en Microsoft Team- eller teamkanal (når du placerer teamets SharePoint-websted i venteposition) blev udgivet d. 22. juni 2017. Hvis et teamwebsted er i venteposition, bevares Wiki-indholdet fra denne dato. Men hvis et teamwebsted er i venteposition, og Wiki-indholdet blev slettet før 22. juni 2017, blev wiki-indholdet ikke bevaret.
