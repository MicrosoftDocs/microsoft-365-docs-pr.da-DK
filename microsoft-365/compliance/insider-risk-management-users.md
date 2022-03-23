---
title: Brugerdashboard for Insiders til risikostyring
description: Få mere at vide om insider-dashboardet Brugere i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
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
ms.openlocfilehash: a690f007b05709b094edd0c9d72417715875dfaf
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2021
ms.locfileid: "63588763"
---
# <a name="insider-risk-management-users-dashboard"></a>Brugerdashboard for Insiders til risikostyring

**Brugerdashboardet** er et vigtigt værktøj i arbejdsprocessen for insider-risikostyring og hjælper virksomheder og analytikere med at få en mere komplet forståelse af risikoaktiviteter. Dette dashboard indeholder visninger og administrationsfunktioner, der opfylder administrative behov mellem oprettelse af insider-politikker til risikostyring og administration af insider-risikostyringssager.

Når brugere er føjet til politikker for insider-risikostyring, evaluerer baggrundsprocesser automatisk brugeraktiviteter til [at udløse indikatorer](insider-risk-management-settings.md#indicators). Når der er udløst indikatorer, tildeles brugeraktiviteterne risikoresultater. Nogle af disse aktiviteter kan resultere i en insider-risikobesked, men nogle aktiviteter opfylder muligvis ikke et minimum for risikoscore, og der oprettes ikke en insider-risikobesked. Med **dashboardet Brugere** kan du få vist brugere med disse typer indikatorer og risikoresultater samt brugere, der har aktive Insider-risikobeskeder.

Få mere at vide om, hvordan dashboardet Brugere viser brugere i følgende scenarier:

- Brugere med besked om aktiv insider-risikopolitik
- Brugere med udløsende hændelser
- Brugere, der er føjet midlertidigt til politikker

## <a name="users-with-active-insider-risk-policy-alerts"></a>Brugere med besked om aktiv insider-risikopolitik

**Dashboardet Brugere** viser automatisk alle brugere med aktive insider-risikopolitikbeskeder. Disse brugere med beskeder har både en udløsende indikator og en aktivitetsscore, der opfylder kravene til oprettelse af en Insider-risikobesked. Aktiviteter for disse brugere vises ved at vælge brugeren i **dashboardet Brugere** og navigere til **fanen Brugeraktivitet** .

## <a name="users-with-triggering-events"></a>Brugere med udløsende hændelser

**Brugerdashboardet** viser automatisk alle brugere med udløsende hændelser, men som ikke har en aktivitets risikoscore, som ville oprette en Insider-risikobesked. Eksempelvis vises en bruger med en rapporteret dato for udfald, fordi denne aktivitet er en udløsende hændelse, men ikke er en aktivitet, der har et risikoresultat. Aktiviteter for disse brugere vises ved at vælge brugeren i **dashboardet Brugere** og navigere til **fanen Brugeraktivitet** .

## <a name="users-added-temporarily-to-policies"></a>Brugere, der er føjet midlertidigt til politikker

**Brugerdashboardet** omfatter brugere, der er føjet til politikker for insider-risikostyring efter en usædvanlig begivenhed uden for insider-risikostyringsarbejdsprocessen. Midlertidig tilføjelse af brugere (fra dashboardet Politikker) er også en metode til at begynde at score brugeraktivitet for en insider-risikostyringspolitik til test af politikken, også selvom en påkrævet forbindelse ikke er konfigureret.

Når en bruger føjes manuelt til en politik, får brugerens aktiviteter de seneste 90 dage point og føjes til **tidslinjen for brugeraktivitet** . Du har f.eks. en bruger, der i øjeblikket ikke får tildelt risikoresultater for en Insider-risikopolitik, og brugeren har rapporteret datalækageaktiviteter til den juridiske afdeling i din organisation. Den juridiske afdeling anbefaler, at du konfigurerer nye kortvarige overvågningskrav til brugeren. Du kan midlertidigt tildele brugeren til din *politik for datalækager* i en bestemt periode (aktiveringsvindue). Alle brugere, der er tilføjet midlertidigt, vises i **brugerdashboardet** , fordi krav til udløserhændelser frafaldes.

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i **brugerdashboardet**. Det kan tage op til 24 timer at få vist aktiviteter for disse brugere i de foregående 90 dage. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere, skal du vælge brugeren på **dashboardet** Brugere og åbne **fanen** Brugeraktivitet i detaljeruden.

Brugeren fjernes automatisk fra dashboardet Brugere, **og pointdeling** stopper, når den tid, der er angivet i **aktiveringsvinduet** , udløber, hvis:

- brugeren ikke har nogen yderligere udløsende hændelser eller insider-risikopolitikbeskeder, og
- hvis den manuelt definerede varighed **af aktiveringsvinduet** er længere end varigheden af den globale politik **Aktiveringsvindue** .

Indstillingen **Aktiveringsvindue** med den længste varighed tilsidesætter altid **indstillingen Aktiveringsvindue** med en kortere varighed. Du har f.eks. konfigureret vinduet  Aktivering under fanen Global **politiks** tidsrammer i de globale indstillinger for insider-risikostyring i 15 dage, som automatisk anvendes på alle dine Insider-risikopolitikker.

Du føjer midlertidigt en bruger til din *politik* for datalækager og definerer 30 dage som **aktiveringsvinduet** for denne bruger. Indstillingen for **den globale aktiveringsvindue** på 15 dage tilsidesættes ved at definere indstillingen  aktiveringsvindue på 30 dage for den midlertidigt tilføjede bruger. Den midlertidigt tilføjede bruger forbliver i **dashboardet Brugere** og er i 30 dage i politikkens område.

I det modsatte scenarie, hvor indstillingen  for det globale aktiveringsvindue er  længere end indstillingen Aktiveringsvindue, der er defineret for en midlertidigt tilføjet bruger, tilsidesætter den globale indstilling af aktiveringsvinduet indstillingen for den midlertidigt tilføjede bruger.  Den midlertidigt tilføjede bruger forbliver i **dashboardet** Brugere og er i omfang for politikken i det antal dage, der er defineret i de globale indstillinger **for aktiveringsvindue** .

## <a name="view-user-information-on-the-users-dashboard"></a>Få vist brugeroplysninger på dashboardet Brugere

Hver enkelt bruger, der vises i **dashboardet Brugere** , har følgende oplysninger:

- **Brugere**: Brugernavnet for en bruger. Dette felt anonymiseres, hvis indstillingen for global anonymisering for Insider Risk Management er aktiveret.
- **Risikoniveau**: Brugerens aktuelle beregnede risikoniveau. Dette resultat beregnes hver 24. time og bruger risikoresultater fra alle aktive beskeder, der er knyttet til brugeren. For brugere, der kun udløser indikatorer, er risikoniveauet nul.
- **Aktive beskeder**: Antallet af aktive beskeder for alle politikker.
- **Bekræftede overtrædelser**: Antallet af tilfælde, der er blevet løst som *en bekræftet overtrædelse* af politikken for brugeren.
- **Sag**: Den aktuelle aktive sag for brugeren.

Hvis du hurtigt vil finde en bestemt bruger, **skal du** bruge Søg i øverste højre hjørne af brugerdashboardet. Når du søger efter brugere, skal du bruge brugerens hovednavn (UPN). Når du f.eks. søger efter en bruger ved navn "Tiara Hidayah", der har et UPN af 'thidayah' i organisationen, skal du skrive 'thidayah' eller en del af UPN'en i **søgning**.

![Insider-dashboard for brugere af risikostyring.](../media/insider-risk-users-dashboard.png)

> [!NOTE]
> Antallet af brugere, der vises på **dashboardet** Brugere, kan i nogle tilfælde være begrænset, afhængigt af mængden af aktive beskeder og politikker, der matcher. Brugere med aktive beskeder vises på dashboardet Brugere,  efterhånden som beskederne genereres, og der kan være sjældne tilfælde, hvor det maksimale antal viste brugere er nået. Hvis denne grænse forekommer, føjes brugere med aktive beskeder, der ikke vises, til brugerdashboardet, efterhånden som eksisterende brugerbeskeder om problemer ændres.

## <a name="view-user-details"></a>Vis brugeroplysninger

Hvis du vil have vist flere oplysninger om risikoaktivitet for en bruger, skal du åbne ruden med brugeroplysninger ved at dobbeltklikke på en bruger i **dashboardet Brugere**. I detaljeruden kan du få vist følgende oplysninger:

- **Fanen Brugerprofil**
  - **Navn og titel**: Brugerens navn og stilling i Azure Active Directory. Disse brugerfelter bliver anonymiserede eller tomme, hvis indstillingen for global anonymisering for insider-risikostyring er aktiveret.
  - **Brugermail**: Brugerens mailadresse.
  - **Alias**: Brugerens netværksalias.
  - **Organisation eller afdeling**: Brugerens organisation eller afdeling.

- **Fanen Brugeraktivitet**
  - **Oversigt over de seneste brugeraktiviteter**: Viser både udløsende indikatorer og Insider-risikoindikatorer for brugeraktiviteter op til de seneste 180 dage. Alle aktiviteter, der er relevante for insider-risikoindikatorer, scores også, selvom aktiviteterne muligvis eller ikke har genereret en insider-risikobesked. Det kan være en dato eller den seneste planlagte arbejdsdato for brugeren, der udløser indikatorekseler. Insider-risikoindikatorer er aktiviteter, der er fastlagt til at have et risikoelement og er defineret i politikker, som brugeren er inkluderet i. Begivenheds- og risikoaktiviteter vises med det seneste element angivet først.

## <a name="remove-users-from-in-scope-assignment-to-policies"></a>Fjern brugere fra en omfangsbaseret tildeling til politikker

Der kan være scenarier, hvor du er nødt til at stoppe med at tildele risikoresultater til en brugers aktivitet i insider-risikostyringspolitikker. Brug **Fjern brugere på** siden med **dashboardet** Brugere til at stoppe med at tildele risikoresultater for en eller flere brugere fra alle insider-risikostyringspolitikker, som de aktuelt er omfattet af. Denne handling fjerner ikke brugere fra den overordnede politiktildeling (når du føjer brugere eller grupper til en politikkonfiguration), men fjerner blot brugerne fra aktiv behandling af politikker efter aktuelle udløserhændelser. Hvis brugerne har en anden udløserhændelse i fremtiden, begynder risikoresultater fra politikker automatisk at blive tildelt til brugerne igen. Eventuelle eksisterende beskeder eller tilfælde for denne bruger fjernes ikke.

> [!NOTE]
> Det kan tage flere minutter at fjerne en bruger fra en politik. Når det er fuldført, vises brugeren ikke længere på siden Brugere. Hvis den fjernede bruger har aktive beskeder eller sager, forbliver brugeren på siden Brugere, og oplysningerne om brugeren viser, at de ikke længere er omfattet af en politik.

Hvis du manuelt vil fjerne brugere fra en omfangsstatus i alle insider-politikker for risikostyring, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring** og vælge **fanen** Brugere.
2. På **dashboardet Brugere skal** du vælge den eller de brugere, du vil fjerne, så de ikke er omfattet af insider-risikostyringspolitikkerne.
3. Vælg **Fjern brugere**.
4. I **ruden Fjern bruger** skal du vælge **Fjern** **eller Annuller** for at annullere ændringerne og lukke dialogboksen.
5. Vælg **Fjern** i bekræftelsesruden for at fjerne brugeren.

## <a name="run-automated-tasks-with-power-automate-flows-for-a-user"></a>Kør automatiserede opgaver med Power Automate flows for en bruger

Ved hjælp Power Automate dataflows kan risikoanalytikere og analytikere hurtigt reagere på:

- Giv brugerne besked, når de føjes til en Insider-risikopolitik

At køre, administrere eller oprette Power Automate flows for en insider-bruger til risikostyring:

1. Vælg **Automatiser** på værktøjslinjen for brugerhandling.
2. Vælg det Power Automate, der skal køres, og vælg **derefter Kør flow**.
3. Når flowet er fuldført, skal du vælge **Udført**.

Du kan få mere at Power Automate om flow for insider-risikostyring under [Introduktion til indstillinger for insider-risikostyring](insider-risk-management-settings.md#power-automate-flows-preview).
