---
title: Konfigurere et team med sikkerhedsisolation i et udviklings-/testmiljø
f1.keywords:
- NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.date: 08/14/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
description: Konfigurer den sikkerhed og infrastruktur, der giver dine medarbejdere mulighed for at arbejde eksternt hvor som helst og når som helst.
ms.openlocfilehash: 8ea359f2c0de98ac35b90a379e5a60c4578e66cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599854"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Konfigurere et team med sikkerhedsisolation i et udviklings-/testmiljø

Denne artikel indeholder en trinvis vejledning i at oprette et team med [sikkerhedsisolation](secure-teams-security-isolation.md) i et udviklings-/testmiljø.

[Konfiguration af et isoleret firmastrategiteam.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Brug dette udviklings-/testmiljø til at eksperimentere og finjustere indstillingerne for dine specifikke behov, før du installerer denne type team i produktion.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Fase 1: Opbyg dit Microsoft 365 Enterprise testmiljø

Hvis du blot ønsker at teste følsomme og meget følsomme teams på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md).

Hvis du vil teste følsomme og meget følsomme teams i en simuleret virksomhed, skal du følge instruktionerne i Synkronisering [af adgangskodehash](../enterprise/password-hash-sync-m365-ent-test-environment.md).

> [!NOTE]
> Test af et team med sikkerhedsisolation kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den findes her som en mulighed, så du kan teste et team med sikkerhedsisolation og eksperimentere med det i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>Fase 2: Opret og konfigurer din Azure Active Directory (Azure AD) gruppe og brugere

I denne fase opretter og konfigurerer du en Azure AD-gruppe og brugere til din fiktive organisation.

Først skal du oprette en sikkerhedsgruppe med Azure-portalen.

1. Opret en separat fane i browseren, og gå derefter til Azure-portalen på [https://portal.azure.com](https://portal.azure.com). Hvis det er nødvendigt, kan du logge på med legitimationsoplysningerne for den globale administratorkonto til din Microsoft 365 E5 eller betalte abonnement.

2. I Azure-portalen skal du klikke **Azure Active Directory > Grupper**.

3. På **bladet Grupper – Alle grupper** skal du klikke **på + Ny gruppe**.

4. På **gruppebladet** :

  - Vælg **Sikkerhed** i **gruppetype**.

  - Skriv **C-Suite** i **Navn**.

  - Vælg **Tildelt** i **Medlemskabstype**.

5. Klik **på Opret**, og luk derefter **gruppebladet** .

Dernæst skal du konfigurere automatisk licensering, så medlemmer af den **nye C-Suite-gruppe** automatisk tildeles Microsoft 365 E5 licens.

1. I Azure-portalen skal du klikke **Azure Active Directory > licenser > Alle produkter**.

2. På listen skal du vælge **Microsoft 365 Enterprise E5** og derefter klikke på **Tildel**.

3. I **bladet Tildel** licens skal du klikke **på Brugere og grupper**.

4. Vælg **C-Suite-gruppen på listen over** grupper.

5. Klik **på Vælg**, og klik derefter på **Tildel**.

6. Luk fanen Azure-portal i din browser.

Dernæst skal [du oprette forbindelse til Azure Active Directory PowerShell til Graph modul](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Udfyld organisationens navn, din placering og en fælles adgangskode, og kør derefter disse kommandoer fra PowerShell-kommandoprompten eller det integrerede scriptmiljø (ISE) for at oprette nye brugerkonti og føje dem til C-Suite-gruppen:

```powershell
$orgName="<organization name, such as contoso-test for the contoso-test.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO")
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> Brug af en fælles adgangskode her er til automatisering og nem konfiguration for et udviklings-/testmiljø. Dette frarådes naturligvis på det kraftigste i forbindelse med produktionsabonnementer.

Brug disse trin til at bekræfte, at gruppebaserede licenser fungerer korrekt.

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com).

2. I den nye **Microsoft 365 Administration i** browseren skal du klikke på **Brugere**.

3. Klik på Administrerende direktør på listen **over brugere**.

4. I ruden, der viser egenskaberne for den  administrerende direktørs brugerkonto, skal du kontrollere, at den er blevet tildelt **Microsoft 365 Enterprise E5-licensen** i **Produktlicenser**.

## <a name="phase-3-create-your-team"></a>Fase 3: Opret dit team

I denne fase opretter og konfigurerer du et team med sikkerhedsisolation, så medlemmer af seniorledelsesteamet kan samarbejde om virksomhedsstrategi.

Du skal først aktivere følsomhedsetiketter for at beskytte indhold i Microsoft Teams, Office 365 og grupper af SharePoint, før du fortsætter med trinnene i [denne artikel](../compliance/sensitivity-labels-teams-groups-sites.md).

Derefter skal du oprette teamet:

1. I Teams skal **du Teams** team i venstre side af appen og derefter klikke på Deltag i eller opret et **team** nederst på teamlisten.
2. Klik **på Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. Bevar **standardindstillingen** på listen Følsomhed.
5. Klik **på Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv **Firmastrategi**, og klik derefter **på** **CreateClose** > .

Dernæst skal du begrænse oprettelsen af private kanaler til ejere af gruppen Firmastrategi.

1. I teamet skal du klikke **på Flere indstillinger** og derefter klikke på **Administrer team**.
2. På fanen **Indstillinger** skal du **udvide Medlemstilladelser**.
3. Fjern markeringen **i afkrydsningsfeltet Tillad medlemmer at oprette private** kanaler.

Herefter skal du konfigurere en følsomhedsmærkat med følgende indstillinger:

- Navnet er Company Strategy
- Kryptering er aktiveret
- Gruppen Virksomhedsstrategi har Co-Author tilladelser

Følg disse trin:

1. Åbn Microsoft 365 Overholdelsescenter vælg **Beskyttelse af oplysninger** under <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Løsninger**</a>.
1. Klik **på Opret en etiket**.
1. Skriv **Firmastrategi** for etiketnavnet.
1. Skriv **Senior Leadership Company Strategy Documents** som værktøjstip, og klik derefter på **Næste**.
1. Vælg **Anvend** på rullelisten **Kryptering** på siden **Kryptering**.
1. Sådan tilføjer du teamtilladelser:<br>
  a. Klik **på Tildel tilladelser**.<br>
  b. Klik **på Tilføj brugere eller grupper**, vælg **Firmastrategi**, og klik derefter på **Tilføj**.<br>
  c. Klik **på Vælg tilladelser**.<br>
  d. Vælg **Samtidig redigering** på rullelisten, og klik derefter på **Gem**.<br>
1. Klik på **Næste**.
1. Klik på **Næste på** siden **Indholdsmærkning**.
1. Angiv Indstillinger **for websted og gruppe** på siden Indstillinger **for websted og gruppe til** **Til**.
1. I **rullemenuen Beskyttelse af Office 365 gruppeforbundne teamwebsteder** skal du vælge **Privat – kun medlemmer kan få adgang til webstedet**.
1. Under **Ikke-administrerede enheder skal** du vælge **Bloker adgang**.
1. Klik på **Næste**.
1. På siden **Automatisk mærkat for Office skal** du klikke på **Næste**.
1. Klik **på Send**, og klik derefter på **Udført**.

Derefter skal du udgive den nye etiket med disse trin:

1. I Microsoft 365 Overholdelsescenter under Beskyttelse <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**af oplysninger skal**</a> du vælge **fanen Etiketpolitikker**.
2. Klik **på Udgiv etiketter**.
3. På siden **Vælg følsomhedsmærkater til publicering** skal du klikke **på Vælg følsomhedsmærkater, der skal publicere**.
4. Vælg **Firmastrategi**, og klik derefter på **Tilføj**.
5. Klik på **Næste**.
6. Klik på **Vælg brugere og grupper på** siden **Publicer til brugere og grupper**.
7. Klik **på** Tilføj, og vælg **derefter Firmastrategi**.
8. Klik **på Tilføj**, og klik derefter på **Udført**.
9. Klik på **Næste**.
10. På siden Politikindstillinger skal du markere afkrydsningsfeltet Brugere skal angive begrundelse for at fjerne en etiket eller et lavere klassificeringsnavn og derefter klikke på **Næste**.
11. Skriv **Firmastrategi** for politikkens navn, og klik derefter på **Næste**.
12. Klik **på Send** , og klik derefter på **Udført**.

Det kan tage lidt tid, før **firmastrategimærkaten** bliver tilgængelig, efter den er blevet publiceret.

Dernæst skal du anvende den nye etiket til **Company Strategy-teamet** og opdatere standardlinktypen for deling for at reducere risikoen for utilsigtet deling af filer og mapper til en bredere målgruppe end beregnet.

1. Åbn SharePoint Administration, og **vælg Aktive websteder** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**under Websteder**</a>.
1. Vælg **webstedet Firmastrategi** .
1. På fanen **Politikker** under Følsomhed **skal** du vælge **Rediger**.
1. Vælg etiketten **Firmastrategi** , og vælg derefter **Gem**.
1. På fanen **Politikker** under Ekstern **deling skal** du vælge **Rediger**.
1. Vælg **Kun personer i organisationen**.
1. Fjern **markeringen i afkrydsningsfeltet** Samme som indstilling på **organisationsniveau under** Standardtype for delingslink, og vælg **Personer med eksisterende adgang**.
1. Vælg **Gem**.

Dernæst skal du konfigurere deling kun for ejere af **virksomhedsstrategiteamet** .

1. I Teams skal du gå til **fanen Generelt** for **firmastrategiteamet**.
2. Klik på Filer på teamets **værktøjslinje**.
3. Klik på ellipsen, og klik derefter **på Åbn i SharePoint**.
4. Klik på ikonet for indstillinger på SharePoint webstedsværktøjslinjen, og klik derefter på **Webstedstilladelser**.
5. I ruden Webstedstilladelser under Deling **af websted skal du** klikke **på Rediger, hvordan medlemmer kan dele**.
6. Under **Delingstilladelser** skal du **vælge Kun webstedsejere kan dele filer, mapper og webstedet** og derefter klikke på **Gem**.
7. Luk tilladelser **og** **Indstillinger** ruder.

Hvis du logger på som medlem af gruppen Virksomhedsstrategi, kan du se Firmastrategi  i følsomhedsindstillingen på værktøjslinjen Hjem i Word, Excel og PowerPoint. Vælg **firmastrategimærkaten** fra **følsomhedsindstillingen** for at tildele navnet til en fil.

Her er den resulterende konfiguration for Firmastrategi-teamet.

![Konfiguration af et isoleret firmastrategiteam.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Næste trin

Når du er klar til produktionsinstallation, skal du se denne [konfigurationsvejledning](secure-teams-security-isolation.md).
