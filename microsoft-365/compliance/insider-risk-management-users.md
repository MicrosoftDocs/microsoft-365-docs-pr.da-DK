---
title: Dashboard for brugere af styring af insiderrisiko
description: Få mere at vide om insiderrisikostyring Brugerdashboard i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 14c0d5127f4b370d78b54512d8780d1cc7dfbf67
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787644"
---
# <a name="insider-risk-management-users-dashboard"></a>Dashboard for brugere af styring af insiderrisiko

**Dashboardet Brugere** er et vigtigt værktøj i arbejdsprocessen for styring af insiderrisiko og hjælper efterforskere og analytikere med at få en mere komplet forståelse af risikoaktiviteter. Dette dashboard indeholder visninger og administrationsfunktioner, der opfylder administrative behov mellem oprettelse af politikker for styring af insiderrisiko og administration af insiderrisikostyringssager.

Når brugerne er føjet til politikker for styring af insiderrisiko, evaluerer baggrundsprocesser automatisk brugeraktiviteter for [udløserindikatorer](insider-risk-management-settings.md#indicators). Når der er udløste indikatorer, tildeles brugeraktiviteterne risikoscores. Nogle af disse aktiviteter kan resultere i en insiderrisikoadvarsel, men nogle aktiviteter opfylder muligvis ikke et minimumniveau for risikoscore, og der oprettes ikke en insiderrisikobesked. **Dashboardet Brugere** giver dig mulighed for at få vist brugere med disse typer indikatorer og risikoscores samt brugere, der har aktive insiderrisikobeskeder.

Få mere at vide om, hvordan dashboardet Brugere viser brugere i følgende scenarier:

- Brugere med aktive beskeder om insiderrisikopolitik
- Brugere med udløsende hændelser
- Brugere, der er føjet midlertidigt til politikker

## <a name="users-with-active-insider-risk-policy-alerts"></a>Brugere med aktive beskeder om insiderrisikopolitik

**Dashboardet Brugere** viser automatisk alle brugere med aktive beskeder om insiderrisikopolitik. Disse brugere med beskeder har både en udløserindikator og en aktivitetsrisikoscore, der opfylder kravene til oprettelse af en insiderrisikobesked. Aktiviteter for disse brugere vises ved at vælge brugeren på **dashboardet Brugere** og navigere til fanen **Brugeraktivitet** .

## <a name="users-with-triggering-events"></a>Brugere med udløsende hændelser

**Dashboardet Brugere** viser automatisk alle brugere med udløsende hændelser, men som ikke har en aktivitetsrisikoscore, der ville oprette en insiderrisikobesked. En bruger med en rapporteret fratrædelsesdato vises f.eks., fordi denne aktivitet er en udløsende hændelse, men ikke en aktivitet, der har en risikoscore. Aktiviteter for disse brugere vises ved at vælge brugeren på **dashboardet Brugere** og navigere til fanen **Brugeraktivitet** .

## <a name="users-added-temporarily-to-policies"></a>Brugere, der er føjet midlertidigt til politikker

**Dashboardet Brugere** indeholder brugere, der er føjet til politikker for styring af insiderrisiko efter en usædvanlig hændelse uden for arbejdsprocessen for styring af insiderrisiko. Midlertidig tilføjelse af brugere (fra dashboardet Politikker) er også en måde at starte scoring af brugeraktivitet for en politik for styring af insiderrisiko for at teste politikken, også selvom en påkrævet connector ikke er konfigureret.

Når en bruger føjes manuelt til en politik, bliver brugeraktiviteterne for de forrige 90 dage scoret og føjet til tidslinjen **Brugeraktivitet** . Du har f.eks. en bruger, der i øjeblikket ikke er tildelt risikoscores for en insiderrisikopolitik, og brugeren har rapporteret datalækageaktiviteter til den juridiske afdeling i din organisation. Den juridiske afdeling anbefaler, at du konfigurerer nye krav til registrering på kort sigt for brugeren. Du kan midlertidigt tildele brugeren til din politik for *datalækager* i et angivet tidsrum (aktiveringsvindue). Alle brugere, der er tilføjet midlertidigt, vises i **dashboardet Brugere** , fordi der er givet afkald på krav om udløsende hændelser.

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i **dashboardet Brugere**. Det kan tage op til 24 timer at vise aktiviteter for de foregående 90 dage for disse brugere. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere, skal du vælge brugeren på **dashboardet Brugere** og åbne fanen **Brugeraktivitet** i detaljeruden.

Brugeren fjernes automatisk fra **dashboardet Brugere** , og scoren stopper, når den tid, der er defineret i **aktiveringsvinduet** , udløber, hvis:

- brugeren ikke har yderligere udløserhændelser eller beskeder om insiderrisikopolitik, og
- hvis den manuelt definerede varighed af **aktiveringsvinduet** er længere end varigheden af den globale politik **Aktiveringsvindue** .

Indstillingen **aktiveringsvindue** med den længstvarende varighed tilsidesætter altid indstillingen **aktiveringsvindue** med en kortere varighed. Du har f.eks. konfigureret **vinduet Aktivering** under fanen Globale **politiktidsrammer** i de globale indstillinger for styring af insiderrisiko i 15 dage, som automatisk anvendes på alle dine insiderrisikopolitikker.

Du føjer midlertidigt en bruger til politikken for insiderrisiko for *datalækager* og definerer 30 dage som **aktiveringsvinduet** for denne bruger. Den globale indstilling **for aktiveringsvinduet** på 15 dage tilsidesættes ved at definere indstillingen for **aktiveringsvinduet** på 30 dage for den midlertidigt tilføjede bruger. Den midlertidigt tilføjede bruger forbliver i **dashboardet Brugere** og er omfattet af politikken i 30 dage.

I det modsatte scenarie, hvor den globale indstilling **for aktiveringsvinduet** er længere end den indstilling for **aktiveringsvinduet** , der er defineret for en bruger, der er tilføjet midlertidigt, tilsidesætter den globale indstilling for **aktiveringsvinduet** **indstillingen for** den midlertidigt tilføjede bruger. Den midlertidigt tilføjede bruger forbliver i **dashboardet Brugere** og er omfattet af politikken for det antal dage, der er defineret i indstillingerne for det globale **aktiveringsvindue** .

## <a name="view-user-information-on-the-users-dashboard"></a>Få vist brugeroplysninger på brugerdashboardet

Hver bruger, der vises i **dashboardet Brugere** , har følgende oplysninger:

- **Brugere**: Brugernavnet for en bruger. Dette felt anonymiseres, hvis den globale indstilling for anonymisering af insiderrisikostyring er aktiveret.
- **Risikoniveau**: Brugerens aktuelle beregnede risikoniveau. Denne score beregnes hvert 24. time og bruger scorerne for beskedrisikoen fra alle aktive beskeder, der er knyttet til brugeren. For brugere, der kun har udløserindikatorer, er risikoniveauet nul.
- **Aktive beskeder**: Antallet af aktive beskeder for alle politikker.
- **Bekræftede overtrædelser**: Antallet af sager, der er løst som *bekræftet politikovertrædelse* for brugeren.
- **Case**: Den aktuelle aktive sag for brugeren.

Hvis du hurtigt vil finde en bestemt bruger, skal du bruge **Søg** øverst til højre på brugerdashboardet. Når du søger efter brugere, skal du bruge brugerens hovednavn (UPN). Når du f.eks. søger efter en bruger med navnet 'Tiara Hidayah', der har et UPN med 'thidayah' i din organisation, skal du angive 'thidayah' eller en del af UPN'et i **Søg**.

![Dashboard for brugere af styring af insiderrisiko.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Antallet af brugere, der vises på **dashboardet Brugere** , kan være begrænset i nogle tilfælde, afhængigt af mængden af aktive beskeder og matchende politikker. Brugere med aktive beskeder vises på **dashboardet Brugere** , efterhånden som beskederne genereres, og der kan være sjældne tilfælde, hvor det maksimale antal viste brugere nås. Hvis denne grænse sker, føjes brugere med aktive beskeder, der ikke vises, til **brugerdashboardet** , efterhånden som eksisterende brugerbeskeder filtreres.

## <a name="view-user-details"></a>Vis brugeroplysninger

Hvis du vil have vist flere oplysninger om risikoaktivitet for en bruger, skal du åbne ruden med brugeroplysninger ved at dobbeltklikke på en bruger på **dashboardet Brugere**. I detaljeruden kan du få vist følgende oplysninger:

- **Fanen Brugerprofil**
  - **Navn og titel**: Brugerens navn og stillingstitel fra Azure Active Directory. Disse brugerfelter anonymiseres eller tomme, hvis den globale indstilling for anonymisering af styring af insiderrisiko er aktiveret.
  - **Brugermail**: Brugerens mailadresse.
  - **Alias**: Brugerens netværksalias.
  - **Organisation eller afdeling**: Brugerens organisation eller afdeling.

- **Fanen Brugeraktivitet**
  - **Oversigt over seneste brugeraktivitet**: Viser både udløsende indikatorer og insiderrisikoindikatorer for brugeraktiviteter op til de sidste 180 dage. Alle aktiviteter, der er relevante for insiderrisikoindikatorer, scores også, selvom aktiviteterne måske eller måske ikke har genereret en insiderrisikoadvarsel. Eksempler på udløsningsindikator kan være en fratrædelsesdato eller den seneste planlagte arbejdsdato for brugeren. Insiderrisikoindikatorer er aktiviteter, der bestemmes for at have et risikoelement og er defineret i politikker, som brugeren er inkluderet i. Hændelses- og risikoaktiviteter vises med det nyeste element angivet først.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Fjern brugere fra tildeling i området til politikker

Der kan være scenarier, hvor du skal stoppe med at tildele scorer for risici til en brugers aktivitet i politikker for styring af insiderrisiko. Brug **Fjern brugere** på **dashboardsiden Brugere** til at stoppe med at tildele scorer for en eller flere brugere fra alle politikker for styring af insiderrisiko, som de i øjeblikket er omfattet af. Denne handling fjerner ikke brugere fra den overordnede politiktildeling (når du føjer brugere eller grupper til en politikkonfiguration), men fjerner blot brugerne fra aktiv behandling af politikker efter aktuelle udløsende hændelser. Hvis brugerne har en anden udløsende hændelse i fremtiden, begynder risikoscores fra politikker automatisk at blive tildelt brugerne igen. Alle eksisterende beskeder eller sager for denne bruger fjernes ikke.

> [!NOTE]
> Det kan tage flere minutter at fuldføre fjernelsen af en bruger fra en politik. Når processen er fuldført, vises brugeren ikke længere på siden Brugere. Hvis den fjernede bruger har aktive beskeder eller sager, forbliver brugeren på siden Brugere, og oplysningerne om brugeren viser, at brugeren ikke længere er omfattet af en politik.

Hvis du manuelt vil fjerne brugere fra in-scope-status i alle politikker for styring af insiderrisiko, skal du fuldføre følgende trin:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Brugere**.
2. På **dashboardet Brugere** skal du vælge den eller de brugere, du vil fjerne fra at være omfattet af området i politikker for styring af insiderrisiko.
3. Vælg **Fjern brugere**.
4. Vælg **Fjern** eller **Annuller** i ruden **Fjern bruger** for at annullere ændringerne og lukke dialogboksen.
5. Vælg **Fjern** i bekræftelsesruden for at fjerne brugeren.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Kør automatiserede opgaver med Power Automate-flow for en bruger

Ved hjælp af anbefalede Power Automate-flow kan risikoforskere og analytikere hurtigt gøre noget for at:

- Giv brugerne besked, når de føjes til en insiderrisikopolitik

Sådan kører, administrerer eller opretter du Power Automate-flow for en bruger af insiderrisikostyring:

1. Vælg **Automatiser** på værktøjslinjen til brugerhandling.
2. Vælg det Power Automate-flow, der skal køres, og vælg derefter **Kør flow**.
3. Når flowet er fuldført, skal du vælge **Udført**.

Du kan få mere at vide om Power Automate-flow til styring af insiderrisiko under [Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#power-automate-flows-preview).
