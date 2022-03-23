---
title: Prøve Microsoft 365 fra mit brugerdefinerede domæne
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Få mere at vide om, hvordan du tester mailfunktionalitet fra mit brugerdefinerede domæne til Microsoft 365 postkasse ved kun at bruge to testkonti.
ms.openlocfilehash: cc977afd32c1b3b660ec01285c36132a8e1d27b2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588254"
---
# <a name="pilot-microsoft-365-from-my-custom-domain"></a>Prøve Microsoft 365 fra mit brugerdefinerede domæne

Du kan prøve Microsoft 365 med disse krav og begrænsninger:

- Din aktuelle mailudbyder skal levere videresendelse af mail.

- Du skal administrere Microsoft 365 DNS-poster hos din DNS-udbyder i stedet for Microsoft 365 at administrere posterne for dig.

    Du kan få mere at vide [under Tilføj DNS-poster for at forbinde dit domæne](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- Oplysninger om ledig/optaget tid for brugere på den anden mailserver er ikke tilgængelige.

- Administratorer kan ikke administrere alle brugerkonti fra en enkelt placering.

- Brugerne kan muligvis ikke bruge filtrering Microsoft 365 uønsket mail.

- Dette anbefales til et meget lille antal brugere og gælder kun for brug af mail til et pilotprojekt.

## <a name="set-up-a-microsoft-365-pilot"></a>Konfigurer en Microsoft 365 pilot

Følg disse trin for at konfigurere et Microsoft 365 pilotprojekt:

### <a name="step-1-sign-in-to-the-microsoft-365-admin-center"></a>Trin 1: Log på Microsoft 365 Administration

1. Log på Microsoft 365 Administration [med](https://admin.microsoft.com) din arbejds- eller skolekonto.

2. Vælg **Indstillinger** >  **domæner i venstre navigationsrude**.

### <a name="step-2-verify-that-you-own-the-domain-you-want-to-use"></a>Trin 2: Bekræft, at du ejer det domæne, du vil bruge

1. På siden **Domæner skal** du vælge **Tilføj domæne**.

2. Skriv domænenavnet i feltet, vælg **Brug dette domæne**, og vælg derefter **Fortsæt**.

3. Vælg de tjenester, du vil teste med dit domæne, f.eks. mail og chat.

4. På siden **Bekræft** domæne skal du følge den trinvise vejledning amd og derefter vælge **Bekræft**.

    Det tager mellem et par minutter og 72 timer, før DNS-ændringer træder i kraft.

    Når bekræftelsen er gennemført, bliver du bedt om at ændre dine DNS-poster.

### <a name="step-3-mark-the-domain-as-shared-in-exchange-online"></a>Trin 3: Markér domænet som delt i Exchange Online

1. I Exchange Administration skal du i sektionen **Mailflow** vælge **Accepterede** domæner og derefter vælge det domæne, du vil ændre.

2. Dobbeltklik for at åbne vinduet, og vælg derefter **Intern videresendelse**.

3. Vælg **Gem**.

    Der kan gå et par minutter, før denne indstilling træder i kraft.

### <a name="step-4-unblock-the-existing-email-server-optional"></a>Trin 4: Fjern blokeringen af den eksisterende mailserver (valgfrit)

Microsoft 365 bruger Exchange Online Protection (EOP) til beskyttelse mod uønsket post. EOP blokerer muligvis din eksisterende mailserver, hvis den registrerer en stor mængde spam, der videresendes af den aktuelle mailserver. Hvis du har tillid til spambeskyttelse for din anden mailudbyder, kan du fjerne blokeringen af serveren Microsoft 365.

> [!NOTE]
> Hvis du fjerner blokeringen af din eksisterende mailserver, kan spam, der modtages via den oprindelige server, komme til Microsoft 365-postkasserne, og du kan ikke evaluere, hvor godt Microsoft 365 forhindrer spam.

1. I navigationsruden Exchange Administration skal du vælge **Beskyttelse** og derefter vælge **Forbindelsesfilter**.

2. På listen **over tilladte IP-adresser** skal du **+** vælge og tilføje IP-adressen på mailserveren for din aktuelle mailudbyder.

### <a name="step-5-create-user-accounts-and-set-the-primary-reply-to-address"></a>Trin 5: Opret brugerkonti, og angiv den primære svar til-adresse

1. I venstre navigationsrude Microsoft 365 Administration vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users.

2. Opret to testkonti ved at tilføje to eksisterende brugere.

    For hver konto skal du **vælge + Tilføj en bruger** og udfylde de nødvendige oplysninger, herunder den adgangskodemetode, du vil teste.

    For at sikre at en brugers mail forbliver **den samme, skal** feltet Brugernavn svare til brugerens aktuelle mailadresse.

3. Vælg den relevante licens, klik på **Næste**, og klik derefter på **Udfør tilføjelse**.

4. Ud **for Brugernavn** skal du vælge dit brugerdefinerede domænenavn på rullelisten.

5. Vælg **CreateClose** > .

### <a name="step-6-configure-mail-to-flow-from-microsoft-365-or-office-365-to-email-server"></a>Trin 6: **Konfigurer mail til at flyde fra Microsoft 365 eller Office 365 til mailserver

Der er to trin til dette:

1. Konfigurer dit Microsoft 365 eller Office 365 miljø.

2. Konfigurer en forbindelse fra Microsoft 365 eller Office 365 til din mailserver.

### <a name="1-configure-your-microsoft-365-or-office-365-environment"></a>1. Konfigurer dit Microsoft 365 eller Office 365 miljø

Sørg for, at du har fuldført følgende i Microsoft 365 eller Office 365:

1. Hvis du vil konfigurere forbindelser, skal du have tildelt tilladelser, før du kan begynde. Hvis du vil kontrollere, hvilke tilladelser du skal bruge, skal Microsoft 365 og Office 365 for forbindelser under [Funktionstilladelser i Exchange Online](/exchange/permissions-exo/feature-permissions) emne.

2. Hvis du vil have EOP eller Exchange Online til at videresende mails fra dine mailservere til internettet, skal du enten:

   - Brug et certifikat, der er konfigureret med et emnenavn, der svarer til et accepteret domæne Microsoft 365 eller Office 365. Vi anbefaler, at certifikatets almindelige navn eller emnealternative navn svarer til organisationens primære SMTP-domæne. Du kan få mere [at vide under Forudsætninger for dit lokale mailmiljø](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#prerequisites-for-your-on-premises-email-environment).

   – ELLER –

   - Sørg for, at alle organisationens afsenderdomæner og underdomæner er konfigureret som accepterede domæner i Microsoft 365 eller Office 365.

   Du kan finde flere oplysninger om definition af accepterede domæner i Administrer accepterede domæner [i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) og [Aktivér mailflow for underdomæner i Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

3. Beslut, om du vil bruge regler for mailflow (også kaldet transportregler) eller domænenavne til at levere mails fra Microsoft 365 eller Office 365 til dine mailservere. De fleste virksomheder vælger at levere mail for alle accepterede domæner. Du kan finde flere oplysninger [i Scenarie: Routing af betinget mail Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing).

> [!NOTE]
> Du kan konfigurere regler for mailflow som beskrevet i [Handlinger til regler for mailflow i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions). Du kan f.eks. bruge regler for mailflow med forbindelser, hvis din mail i øjeblikket dirigeres via distributionslister til flere websteder.

### <a name="2-set-up-a-connector-from-microsoft-365-or-office-365-to-your-email-server"></a>2. Konfigurer en forbindelse fra Microsoft 365 eller Office 365 til din mailserver

Hvis du vil oprette en Microsoft 365 eller Office 365 forbindelse,  >  skal **du vælge Administrator Exchange** for at Exchange Administration. Vælg derefter **mailflowConnectors** > .<a href="https://go.microsoft.com/fwlink/?linkid=2183136" target="_blank"></a>

Konfigurer forbindelser ved hjælp af guiden.

Klik på plustegnet for at starte guiden **+**. På det første skærmbillede skal du **vælge Fra** Office 365 **og Til** din organisations mailserver.

Klik **på** Næste, og følg vejledningen i guiden. Klik på **linkene Hjælp** eller **Få mere at vide** , hvis du har brug for flere oplysninger. Guiden fører dig gennem konfigurationen. Til sidst skal du sikre dig, at forbindelsen validerer. Hvis forbindelsen ikke [valideres](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors) , skal du dobbeltklikke på den viste meddelelse for at få flere oplysninger og se Valider forbindelser for at få hjælp til at løse problemer.



### <a name="step-7-update-dns-records-at-your-dns-hosting-provider"></a>Trin 7: Opdatere DNS-poster hos din DNS-udbyder

Log på DNS-udbyderens websted, og følg vejledningen på Tilføj [DNS-poster for at oprette forbindelse til dit domæne](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Gør følgende to undtagelser:**

- Du må ikke oprette en ny MX-post eller ændre den eksisterende MX-post.

- Hvis du allerede har en SPF (Sender Policy Framework)-post for din tidligere mailudbyder, skal du i stedet for at oprette en ny SPF-post (TXT) for Exchange Online tilføje "include:spf.protection.outlook.com" til den aktuelle TXT-post.

    For eksempel omfatter "v=spf1 mx:adatum.com include:spf.protection.outlook.com ~all".

    Hvis du ikke har en SPF-post, skal du ændre den, der anbefales af Microsoft 365, så den medtager domænet for din aktuelle mailudbyder og tilføjer spf.protection.outlook.com. Dette tillader udgående meddelelser fra begge mailsystemer.

### <a name="step-8-set-up-email-forwarding-at-your-current-provider"></a>Trin 8: Konfigurer videresendelse af mail hos din nuværende udbyder

Hos din nuværende mailudbyder skal du konfigurere videresendelse for dine brugeres mailkonti til dit onmicrosoft.com domæne:

- Videresende bruger en postkasse til usera@yourcompany.onmicrosoft.com

- Videresende bruger B-postkasse til userb@yourcompany.onmicrosoft.com

Når du har fuldført dette trin, er alle mails, der usera@yourcompany.com og userb@yourcompany.com, tilgængelige i Microsoft 365.

> [!NOTE]
> Kontakt din nuværende mailudbyder for at få de nøjagtige trin til at konfigurere videresendelse af mail.<br/>
> Du behøver ikke at beholde en kopi af meddelelserne hos den aktuelle mailudbyder.<br/>
> De fleste udbydere videresender mail ved at lade afsenderens Svar til-adresse forblive intakt, så svar sendes til den oprindelige afsender.

### <a name="step-9-test-mail-flow"></a>Trin 9: Test af mailflow

1. Log på Outlook Web App legitimationsoplysningerne for bruger A.

2. Udfør disse test:

    - Test lokal Microsoft-mail ved at sende en mail til f.eks. bruger B. Mailen leveres straks. I dette scenarie dirigeres meddelelsen ikke til postkassen for Bruger B på den oprindelige server, fordi Microsoft 365 postkassen er lokal.

    - Test mail til en bruger på det eksisterende mailsystem ved at sende en mail til f.eks. bruger C. Mailen leveres til postkassen for bruger C på den oprindelige mailserver.

    - Kontrollér, at videresendelse er konfigureret korrekt fra en ekstern konto eller fra en medarbejdermailkonto på det eksisterende mailsystem. F.eks. skal du fra den oprindelige serverkonto for bruger C eller en Hotmail-konto sende en mail til bruger A og bekræfte, at de modtages i Microsoft 365 for bruger A.

### <a name="step-10-move-mailbox-contents"></a>Trin 10: Flyt postkasseindhold

Da du kun flytter to testbrugere, og bruger A og bruger B begge bruger Outlook, kan du flytte mailen ved at åbne den gamle . PST-fil i den Outlook-profil og kopiere meddelelser, kalenderelementer, kontakter osv. Få mere at vide under [Importér mail, kontakter og kalender fra en Outlook .pst-fil](https://support.microsoft.com/office/import-email-contacts-and-calendar-from-an-outlook-pst-file-431a8e9a-f99f-4d5f-ae48-ded54b3440ac).

Når de er importeret til de relevante placeringer i Microsoft 365, kan elementerne åbnes fra en hvilken som helst enhed, hvor som helst.
