---
title: Brug Microsoft Teams klasser med Blackboard Learn Ultra
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Brug Microsoft Teams klasser med Blackboard Learn Ultra
ms.openlocfilehash: 2cf6c3f3e7c9c8b0004ea08fccdec981c032a491
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63595989"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Brug Microsoft Teams klasser med Blackboard Learn Ultra

Teamwork er kernen i enhver moderne organisation. Ved at fremme samarbejde er det en definition af en egenskab, der definerer enhver vellykket institution. Du kan forbedre alle funktionerne i Blackboard Learn Ultra ved at parre dem med Microsoft Teams klasser.

Dine klasser kan omfatte samtaler i realtid, videomøder eller asynkrone interaktioner. Du kan tilføje fildeling og cocreationsoplevelser til dine studerende, alt sammen på ét sted. Microsoft Teams klasser med Learn Ultra omdefinere dynamicsen inden for undervisning, og hvad effektiv læring betyder.

> [!IMPORTANT]
> Sørg for, at du har konfigureret feltet Institutionsmail i dit [informationssystem for studerende (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>Integration Microsoft Teams-klasser afhænger af institutionens mailfelt i din SIS for at kunne knyttes til de korrekte Microsoft Azure Active Directory (AAD) [UPN (User Principle Name).](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes) Hvis ingen institutionsmail er blevet klargjort, vil dette som standard være den eksisterende mail. Det anbefales, at dette felt angives for hver bruger for at sikre, at deres data synkroniseres korrekt, og at der ikke er nogen konflikt mellem maildata mellem AAD og Blackboard Learn Ultra.
>
> Hvis du ikke har angivet dette felt korrekt i DIN SIS-tilknytning, fungerer integrationen fortsat, men brugerne vises muligvis ikke i de Teams-klasser, der oprettes, og der kan opstå fejl.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Understøttelse af institutionsdatatilknytning – Institution Email SIS-felt

Som en del af udviklingen med cloududbyderintegrationerne har Blackboard Learn Ultra oprettet et nyt  mailfelt for institutionen, både i Student Information System Framework-integration og offentlige REST-API'er, så institutionen kan administrere datasynkroniseringsprocessen effektivt mellem Blackboard Learn Ultra og AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Hvad betyder institutionens mail, og hvad understøtter den?

Feltet **Institution Email** giver mulighed for tilpassede felttilknytninger mellem en klients eksternt understøttede datakilder og Blackboard Learn Ultra. Hvis datakilder er skybaserede udbydere, f.eks. Microsoft, er UPN (User Principle Name) et primært entydig identifier for hver bruger, der består af et UPN-præfiks (brugerens kontonavn) og et UPN-suffiks (et DNS-domænenavn) sammen med et @-symbol. Dette opretter en entydig mailadresse for hver enkelt bruger i Microsoft Azure Active Directory.

For at sikre at data er nøjagtige, og tilmeldinger eller medlemskaber mellem Blackboard Learn Ultra og Microsoft Teams-klasser opnås korrekt, skal en brugers mailadresse svare til begge systemer. I Blackboard Learn Ultra kan brugere ændre eller tilsidesætte deres eksisterende mailadresse i brugergrænsefladen, hvilket kan medføre synkroniseringsfejl, og at brugeren ikke bliver føjet korrekt til et klasseteam. Tilknytning **af feltet Institution** Email sikrer, at dette niveau af sikkerheds- og valideringskontrol kan administreres korrekt, uanset om brugerne har ændret deres mail i Blackboard Learn Ultra eller ej.

 Når to mailadresser er forskellige, enten:

- Der skal tages en beslutning om, hvilken kilde der har forrang, og den skal tages som både person- og institutionsmails.
  Eller
- En institution kan angive et brugerdefineret felttilknytning i sin institutionsmail, som kan løse en potentiel konflikt.

Institution **Email-felttilknytning** er nu tilgængelig for alle eksisterende SIS-integrationstyper i **Advanced Configuration Indstillinger** >  **Users Learn Object** **TypeField-tilknytning** > .

> [!NOTE]
> Det er vigtigt at bemærke, at institutionens mail som standard  er indstillet til **personmail** for alle SIS-formater og skal være entydig for hver person. Alle eksisterende integrationer, der er konfigureret og kører, får denne datatilknytning på plads, da SIS ikke kan importere brugere, hvis deres mail duplikeres. Hvis en institution kræver mulighed for at ændre institutionens mail til **brugerdefineret, skal** de administrere dette via Advanced **Configuration Indstillinger** i SIS.

## <a name="requirements"></a>Krav

Integration Microsoft Teams klasser er kun tilgængelig for **Ultra Course View-kurser**. Din institution skal opfylde disse krav for at bruge den:

- Få Blackboard Learn Ultra Learn SaaS med Ultra Base Navigation aktiveret

  ![Et eksempel på funktionen er aktiveret på kurser.](media/feature-availability.png)

- Aktivere LTI til brug på kurser.

  a. Gå til Administrator **PanelLTI** >  **Tool ProvidersManage** >  **globale egenskaber**.

  b. Vælg **LTI Aktiveret på kurser**, og du kan også vælge **Aktiveret i organisationer**.

  c. Vælg **Send**.

- LTI skal være konfigureret

- Tilføj Blackboard Learn Ultra Teams integration af LTI-klasser

- Tilføj Microsoft Teams klasse LTI 1.3-værktøj

- Tilføj REST API-værktøjet og ressourcedeling på tværs af oprindelser

- Konfigurere og godkende Microsoft Teams integration af klasser

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Tilføj Blackboard Learn Ultra Teams klasse LTI 1.3-værktøjet

1. Vælg **LTI-værktøjsudbydere i Administratorpanel**.

2. Vælg **Registrer LTI 1.3-værktøjet**.

3. I feltet **Klient-id** skal du skrive eller kopiere og indsætte dette id:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Gennemgå alle indstillinger, der er udfyldt på forhånd, og som er angivet i **Status for værktøj**, og vælg derefter **Aktiveret**.

5. I **Institutionspolitikker** skal **du vælge Rolle i Kursus, Navn** **og Mailadresse** og derefter vælge **Ja** for begge.

6. Vælg **Tillad tjenesteadgang til karakterer** **og Tillad adgang til medlemskabstjeneste**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Tilføj værktøjet Microsoft Teams klasse LTI 1.3

1. Vælg **LTI-værktøjsudbydere i Administratorpanel**.

2. Vælg **Registrer LTI 1.3-værktøjet**.

3. I feltet **Klient-id** skal du skrive eller kopiere og indsætte dette id:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Gennemse alle indstillinger, der er udfyldt på forhånd, og vælg Aktiveret i *Status* for *værktøj.*

5. I **Institutionspolitikker** skal **du vælge Rolle i Kursus, Navn** **og Mailadresse**. Vælg **Ja** for begge dele.

6. Vælg **Tillad tjenesteadgang til karakterer** **og Tillad adgang til medlemskabstjeneste**.

## <a name="add-the-rest-api-tool"></a>Tilføj REST-API-værktøjet

1. Fra **administratorpanelet skal du** gå til **Integrationer og** vælge **Rest API-integrationer**.

2. Vælg **Opret integration**.

3. I feltet **Program-id** skal du skrive eller kopiere og indsætte dette id:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Indtast en bruger for denne integration.

   Denne bruger bliver den med start-API-adgang, hvorfra programmet er tilknyttet.

5. Vælg **Send**.

## <a name="add-the-cross-origin-resource-sharing"></a>Tilføj Ressourcedeling på tværs af oprindelse

1. Fra **administratorpanelet skal** du gå til **Integrationer** og vælge **Ressourcedeling på tværs af oprindelser*.

2. Vælg **Opret konfiguration**.

3. I feltet **Origin** skal du skrive kopiér og indsæt denne URL-adresse:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. I feltet **Tilladte sidehoveder** skal du skrive **Godkendelse**.

5. Angiv **Tilgængelig** til **Ja**.

6. Vælg **Send**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Konfigurere og godkende Microsoft Teams integration af klasser

For at integrere din Blackboard Learn Ultra-forekomst med Microsoft Teams-klasser skal du sikre dig, at programmet Blackboard Learn Ultra er godkendt til adgang i din Microsoft Azure-lejer. Dette er en proces, der skal udføres af din institutions Microsoft 365 globale administrator.

Denne proces kan udføres enten før eller efter, at du har konfigureret LTI-programmerne i din Blackboard Learn Ultra-forekomst.

### <a name="before-configuring-the-lti-applications"></a>Før du konfigurerer LTI-programmerne

Hvis du vælger at godkende Blackboard Learn Ultra Teams Classes Azure-appen, før du konfigurerer LTI-integrationerne, skal du omdirigere til **Microsoft Identity Platform**' slutpunkt for administratorsamtykke. URL-adressen vises:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Du skal erstatte **{Tenant} med dit** specifikke institutions-Microsoft Azure lejer-id.

Du får vist et tilladelsesvindue, der forklarer, at du giver tilladelse til Blackboard Learn Ultra til at få adgang Microsoft Teams.

![tilladelsesvinduet for Microsoft og Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Efter konfiguration af LTI-programmerne

1. I **administratorpanelet skal du** gå til **Værktøjer og funktioner og** vælge **Microsoft Teams integrationsadministrator**.

2. Vælg **Aktivér Microsoft Teams**.

3. Tilføj dit **Microsoft-lejer-id** i det tilgængelige tekstfelt.

4. Vælg en af følgende indstillinger:

   - Hvis appen har forudsamtykke, vises der en lille markering. Hvis afkrydsningsfeltet vises, skal du vælge **Send**.

   - Hvis samtykke ikke er blevet godkendt, skal du følge de trin, der er beskrevet for at generere URL-adressen til godkendelse, og sende den Microsoft 365 globale administrator til godkendelse.

5. Når du har bekræftet godkendelsen, skal du **vælge Prøv igen for** at bekræfte og derefter vælge **Send**.
