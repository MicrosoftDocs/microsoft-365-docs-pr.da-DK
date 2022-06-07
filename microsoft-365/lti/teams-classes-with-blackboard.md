---
title: Brug Microsoft Teams-hold med Blackboard Learn Ultra
ms.author: danismith
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
description: Brug Microsoft Teams-hold med Blackboard Learn Ultra
ms.openlocfilehash: f5e53c54db893a184a5b2afe86b61c823b62f5a6
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923056"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>Brug Microsoft Teams-hold med Blackboard Learn Ultra

Teamwork er kernen i alle moderne organisationer. Ved at fremme samarbejdet er det en definerende egenskab ved enhver vellykket institution. Du kan forbedre alle funktionerne i Blackboard Learn Ultra ved at parre dem med Microsoft Teams-klasser.

Dine klasser kan omfatte samtaler i realtid, videomøder eller asynkrone interaktioner. Du kan tilføje fildelings- og cocreation-oplevelser for dine studerende på ét sted. Microsoft Teams-klasser med Learn Ultra omdefinerer dynamikken i undervisningen, og hvad effektiv læring betyder.

> [!IMPORTANT]
> Sørg for, at du har konfigureret feltet InstitutionMail i dit [informationssystem for studerende (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>Integration af Microsoft Teams-klasser afhænger af mailfeltet institution i dit SIS for at kunne knyttes til det korrekte [UPN (User Principle Name](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) for Microsoft Azure Active Directory (AAD). Hvis der ikke er klargjort nogen institutionsmail, vil dette som standard være den eksisterende mail. Det anbefales, at dette felt angives for hver bruger for at sikre, at deres data synkroniseres korrekt, og at der ikke er nogen konflikt mellem maildata mellem AAD og Blackboard Learn Ultra.
>
> Hvis du ikke har angivet dette felt korrekt i din SIS-tilknytning, fungerer integrationen fortsat, men brugerne vises muligvis ikke i de Teams-klasser, der er oprettet, og der kan opstå fejl.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>Understøttende institutionel datatilknytning – Feltet Institutionsmail SIS

Som en del af udviklingen med cloududbyderintegrationer har Blackboard Learn Ultra oprettet et nyt **felt af typen Institution Email** , både i integration af Student Information System Framework og offentlige REST API'er, hvilket giver institutionerne mulighed for at administrere datasynkroniseringsprocessen effektivt mellem Blackboard Learn Ultra og AAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>Hvad betyder institutionens e-mail, og hvad understøtter den?

Feltet **Institution-mail** gør det muligt at tilpasse felttilknytninger mellem en klients eksternt understøttede datakilder og Blackboard Learn Ultra. Hvis datakilder er cloududbydere, f.eks. Microsoft, er UPN (User Principle Name) et primært entydigt id for hver bruger, der består af et UPN-præfiks (brugerens kontonavn) og et UPN-suffiks (et DNS-domænenavn), der er forbundet med et @-symbol. Dette opretter en entydig mailadresse for hver bestemt bruger i Microsoft Azure Active Directory.

For at sikre at dataene er nøjagtige, og at tilmeldinger eller medlemskaber mellem Blackboard Learn Ultra- og Microsoft Teams-klasserne opnås korrekt, skal en brugers mailadresse matche mellem begge systemer. I Blackboard Learn Ultra kan brugerne ændre eller tilsidesætte deres eksisterende mailadresse i brugergrænsefladen, hvilket kan medføre synkroniseringsfejl, og brugeren ikke føjes korrekt til et klasseteam. Felttilknytningen **Institution Email** sikrer, at dette sikkerhedsniveau og valideringskontrol kan administreres korrekt, uanset om brugerne har ændret deres mail i Blackboard Learn Ultra eller ej.

 Når to mailadresser er forskellige, enten:

- Der skal træffes en beslutning om, hvilken kilde der har forrang, og den skal træffes som både person- og institutionmails.
  Eller
- En institution kan angive en brugerdefineret felttilknytning i sin institutionmail, hvilket kan løse en potentiel konflikt.

Felttilknytningen **institutionmail** er nu tilgængelig for alle eksisterende SIS-integrationstyper under **Avancerede konfigurationsindstillinger** > **Brugere Lære felttilknytning for objekttype** > .

> [!NOTE]
> Det er vigtigt at bemærke, at **institutionens mail** som standard er angivet til **Personmail** for alle SIS-formater og skal være entydig for hver person. Alle eksisterende integrationer, der er konfigureret og kører, har denne datatilknytning på plads, da SIS ikke kan importere brugere, hvis deres mail er duplikeret. Hvis en institution kræver mulighed for at ændre institutionmailen til **brugerdefineret**, skal vedkommende administrere dette via **Avancerede konfigurationsindstillinger** i SIS.

## <a name="requirements"></a>Krav

Integration af Microsoft Teams-klasser er kun tilgængelig for **kurser i Ultra Course View**. Din institution skal opfylde disse krav for at kunne bruge den:

- Få Blackboard Learn Ultra Learn SaaS med Ultra Base Navigation aktiveret

  ![et eksempel på funktionen er aktiveret i kurser.](media/feature-availability.png)

- Aktivér LTI til brug i kurser.

  a. Gå til **administratorpanelet** > **LTI-værktøjsprovidere** > **Administrer globale egenskaber**.

  b. Vælg **LTI aktiveret i kurser**, og vælg eventuelt **Aktiveret i organisationer**.

  c. Vælg **Send**.

- LTI skal være konfigureret

- Tilføj Blackboard Learn Ultra Teams-klasser LTI-integration

- Tilføj værktøjet Microsoft Teams Classes LTI 1.3

- Tilføj REST API-værktøjet og ressourcedeling på tværs af oprindelser

- Konfigurer og godkend Integration af Microsoft Teams-klasser

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>Tilføj værktøjet Blackboard Learn Ultra Teams-klasser LTI 1.3

1. Vælg **LTI-værktøjsprovidere** i **administratorpanelet**.

2. Vælg **registrer LTI 1.3 Tool**.

3. I feltet **Klient-id** skal du skrive eller kopiere og indsætte dette id:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Gennemse alle indstillinger, der er udfyldt på forhånd, i **Værktøjsstatus**, og vælg derefter **Aktiveret**.

5. I **Institutionspolitikker** skal du vælge **Rolle i kursus, Navn** og **Mailadresse** og derefter vælge **Ja** for begge.

6. Vælg **Tillad tjenesteadgang til bedømmelse** og **Tillad adgang til medlemskabstjeneste**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>Tilføj værktøjet Microsoft Teams Classes LTI 1.3

1. Vælg **LTI-værktøjsprovidere** i **administratorpanelet**.

2. Vælg **registrer LTI 1.3 Tool**.

3. I feltet **Klient-id** skal du skrive eller kopiere og indsætte dette id:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. Gennemse alle indstillinger, der er udfyldt på forhånd, og vælg Aktiveret i *Værktøjsstatus**.*

5. I **Institutionspolitikker** skal du vælge **Rolle i kursus, Navn** og **Mailadresse**. Vælg **Ja** for begge.

6. Vælg **Tillad tjenesteadgang til bedømmelse** og **Tillad adgang til medlemskabstjeneste**.

## <a name="add-the-rest-api-tool"></a>Tilføj REST API-værktøjet

1. Gå til **Integrationer** i **administratorpanelet**, og vælg **Rest API-integrationer**.

2. Vælg **Opret integration**.

3. I feltet **Program-id** skal du skrive eller kopiere og indsætte dette id:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. Skriv en bruger til denne integration.

   Denne bruger vil være den med start-API-adgang, som programmet er tilknyttet fra.

5. Vælg **Send**.

## <a name="add-the-cross-origin-resource-sharing"></a>Tilføj ressourcedeling på tværs af oprindelser

1. Gå til **Integrationer** i **panelet Administrator**, og vælg **Ressourcedeling på tværs af oprindelser*.

2. Vælg **Opret konfiguration**.

3. I feltet **Oprindelse** skal du kopiere og indsætte denne URL-adresse:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. I feltet **Tilladte brevhoveder** skal du skrive **Autorisation**.

5. Angiv **Tilgængelig** til **Ja**.

6. Vælg **Send**.

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>Konfigurer og godkend integration af Microsoft Teams-klasser

Hvis du vil integrere din Blackboard Learn Ultra-forekomst med Microsoft Teams-klasser, skal du sikre dig, at Blackboard Learn Ultra-programmet er godkendt til at få adgang i din Microsoft Azure-lejer. Dette er en proces, der skal fuldføres af din institutions globale administrator i Microsoft 365.

Denne proces kan udføres enten før eller efter, at du har konfigureret LTI-programmerne i din Blackboard Learn Ultra-forekomst.

### <a name="before-configuring-the-lti-applications"></a>Før du konfigurerer LTI-programmerne

Hvis du vælger at godkende Azure-appen Learn Ultra Teams-klasser på Blackboard, før du konfigurerer LTI-integrationerne, skal du omdirigere til slutpunktet for **administratorsamtykke for Microsoft-identitetsplatform**. URL-adressen vises:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> Du skal erstatte **{Tenant}** med dit specifikke institutionelle Microsoft Azure-lejer-id.

Du får vist et tilladelsesvindue, der forklarer, at du giver tilladelse til Blackboard Learn Ultra for at få adgang til Microsoft Teams.

![tilladelsesvinduet til Microsoft og Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>Efter konfiguration af LTI-programmerne

1. Gå til **Værktøjer og hjælpeprogrammer** i **administratorpanelet**, og vælg **Microsoft Teams Integration Admin**.

2. Vælg **Aktivér Microsoft Teams**.

3. Føj dit **Microsoft-lejer-id** til det tilgængelige tekstfelt.

4. Vælg en af følgende indstillinger:

   - Hvis appen har forhåndsgodkendelse, vises et lille flueben. Hvis markeringen vises, skal du vælge **Send**.

   - Hvis samtykket ikke er blevet godkendt, skal du følge de trin, der er beskrevet, for at generere URL-adressen til samtykke og sende den til den globale administrator for Microsoft 365 til godkendelse.

5. Når du har bekræftet godkendelsen, skal du vælge **Prøv igen** for at bekræfte og derefter vælge **Send**.
