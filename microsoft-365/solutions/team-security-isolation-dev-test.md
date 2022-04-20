---
title: Konfigurer et team med sikkerhedsisolation i et udviklings-/testmiljø
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
description: Konfigurer den sikkerhed og infrastruktur, der gør det muligt for dine medarbejdere at arbejde eksternt overalt og når som helst.
ms.openlocfilehash: 0e54d3840e9207fd7e8b5c50415ad2ca60751059
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934241"
---
# <a name="configure-a-team-with-security-isolation-in-a-devtest-environment"></a>Konfigurer et team med sikkerhedsisolation i et udviklings-/testmiljø

Denne artikel indeholder en trinvis vejledning til, hvordan du opretter et [team med sikkerhedsisolation](secure-teams-security-isolation.md) i et udviklings-/testmiljø.

[Konfiguration for det isolerede team for virksomhedsstrategi.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

Brug dette udviklings-/testmiljø til at eksperimentere og finjustere indstillinger til dine specifikke behov, før du udruller denne type team i produktion.

## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 Enterprise testmiljø

Hvis du kun vil teste følsomme og meget følsomme teams på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af Letvægtsbase](../enterprise/lightweight-base-configuration-microsoft-365-enterprise.md).

Hvis du vil teste følsomme og meget følsomme teams i en simuleret virksomhed, skal du følge vejledningen i [synkronisering af adgangskodehash](../enterprise/password-hash-sync-m365-ent-test-environment.md).

> [!NOTE]
> Test af et team med sikkerhedsisolation kræver ikke det simulerede virksomhedstestmiljø, som omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste et team med sikkerhedsisolering og eksperimentere med det i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-create-and-configure-your-azure-active-directory-azure-ad-group-and-users"></a>Fase 2: Opret og konfigurer din Azure Active Directory (Azure AD) gruppe og brugere

I denne fase opretter og konfigurerer du en Azure AD-gruppe og brugere til din fiktive organisation.

Først skal du oprette en sikkerhedsgruppe med Azure Portal.

1. Opret en separat fane i din browser, og gå derefter til Azure Portal på [https://portal.azure.com](https://portal.azure.com). Hvis det er nødvendigt, skal du logge på med legitimationsoplysningerne for den globale administratorkonto for din Microsoft 365 E5 prøveperiode eller dit betalte abonnement.

2. Klik på **Azure Active Directory > Grupper i Azure Portal**.

3. Klik på **+ Ny gruppe** på bladet **Grupper – alle grupper**.

4. På bladet **Gruppe** :

  - Vælg **Sikkerhed** i **gruppetype**.

  - Skriv **C-Suite** i **navnet**.

  - Vælg **Tildelt** i **medlemskabstype**.

5. Klik på **Opret**, og luk derefter bladet **Gruppe** .

Konfigurer derefter automatisk licensering, så medlemmer af den nye **C-Suite-gruppe** automatisk tildeles en Microsoft 365 E5 licens.

1. Klik på **Azure Active Directory > Licenser > Alle produkter i Azure Portal**.

2. Vælg **Microsoft 365 Enterprise E5** på listen, og klik derefter på **Tildel**.

3. Klik på **Brugere og grupper** under bladet **Tildel licens**.

4. Vælg gruppen **C-Suite** på listen over grupper.

5. Klik på **Vælg**, og klik derefter på **Tildel**.

6. Luk fanen Azure Portal i browseren.

Derefter [skal du oprette forbindelse til modulet Azure Active Directory PowerShell til Graph](../enterprise/connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Udfyld organisationens navn, din placering og en fælles adgangskode, og kør derefter disse kommandoer fra PowerShell-kommandoprompten eller ISE (Integrated Script Environment) for at oprette nye brugerkonti og føje dem til C-Suite-gruppen:

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
> Brug af en almindelig adgangskode her er til automatisering og nem konfiguration af et udviklings-/testmiljø. Dette frarådes naturligvis i høj grad for produktionsabonnementer.

Brug disse trin til at kontrollere, at gruppebaserede licenser fungerer korrekt.

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com).

2. Klik på **Brugere** på den nye **fane Microsoft 365 Administration** i browseren.

3. Klik på **CEO** på listen over brugere.

4. Kontrollér, at den er tildelt **Microsoft 365 Enterprise E5-licensen** i Produktlicenser i den rude, der viser egenskaberne for den **administrerende** **direktør-brugerkonto**.

## <a name="phase-3-create-your-team"></a>Fase 3: Opret dit team

I denne fase opretter og konfigurerer du et team med sikkerhedsisolering, så medlemmer af det øverste ledelsesteam kan samarbejde om virksomhedens strategi.

Aktivér først følsomhedsmærkater for at beskytte indhold i Microsoft Teams, Office 365 grupper og SharePoint websteder, før du fortsætter med trinnene i [denne artikel](../compliance/sensitivity-labels-teams-groups-sites.md).

Opret derefter teamet:

1. I Teams skal du klikke på **Teams** i venstre side af appen og derefter klikke på **Deltag eller opret et team** nederst på listen over teams.
2. Klik på **Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. Bevar standarden på listen **Følsomhed** .
5. Klik på **Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv **Firmastrategi**, og klik derefter på **OpretLuk** > .

Derefter skal du begrænse oprettelsen af private kanaler til ejere af gruppen Virksomhedsstrategi.

1. Klik på **Flere indstillinger** i teamet, og klik derefter på **Administrer team**.
2. Udvid **Medlemstilladelser** under fanen **Indstillinger**.
3. Fjern markeringen i afkrydsningsfeltet **Tillad, at medlemmer opretter private kanaler** .

Derefter skal du konfigurere en følsomhedsmærkat med følgende indstillinger:

- Navnet er Firmastrategi
- Kryptering er aktiveret
- Gruppen Virksomhedsstrategi har Co-Author tilladelser

Følg disse trin:

1. Åbn Microsoft Purview-overholdelsesportalen under **Løsninger**, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Information Protection**</a>.
1. Klik på **Opret en etiket**.
1. Skriv **Firmastrategi** for navnet.
1. Skriv **Dokumenter med strategi for ledelsesfirma** som værktøjstip, og klik derefter på **Næste**.
1. På siden **Kryptering** på rullelisten **Kryptering** skal du vælge **Anvend**.
1. Sådan tilføjer du teamtilladelserne:<br>
  a. Klik på **Tildel tilladelser**.<br>
  b. Klik på **Tilføj brugere eller grupper**, vælg **Firmastrategi**, og klik derefter på **Tilføj**.<br>
  c. Klik på **Vælg tilladelser**.<br>
  d. Vælg **Medforfatter** på rullelisten, og klik derefter på **Gem**.<br>
1. Klik på **Næste**.
1. Klik på **Næste** på siden **Indholdsmarkering**.
1. På siden **Indstillinger for websted og gruppe** skal du angive **Indstillinger for websted og gruppe** til **Til**.
1. På rullelisten **Beskyttelse af personlige oplysninger for Office 365 gruppetilsluttede teamwebsteder** skal du vælge **Privat – kun medlemmer kan få adgang til webstedet**.
1. Under **Ikke-administrerede enheder** skal du vælge **Bloker adgang**.
1. Klik på **Næste**.
1. Klik på **Næste** på siden **Automatisk mærkning af Office apps**.
1. Klik på **Send**, og klik derefter på **Udført**.

Publicer derefter den nye mærkat med disse trin:

1. På Microsoft Purview-overholdelsesportalen under <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Beskyttelse af oplysninger**</a> skal du vælge fanen **Mærkatpolitikker** .
2. Klik på **Publicer navne**.
3. På siden **Vælg følsomhedsmærkater, der skal udgives** skal du klikke på **Vælg følsomhedsmærkater, der skal publiceres**.
4. Vælg **Firmastrategi**, og klik derefter på **Tilføj**.
5. Klik på **Næste**.
6. På siden **Publicer til brugere og grupper** skal du klikke på **Vælg brugere og grupper**.
7. Klik på **Tilføj**, og vælg derefter **Virksomhedsstrategi**.
8. Klik på **Tilføj**, og klik derefter på **Udført**.
9. Klik på **Næste**.
10. På siden Politikindstillinger skal du markere afkrydsningsfeltet **Brugere skal angive begrundelse for at fjerne en etiket eller en lavere klassificeringsmærkat** og derefter klikke på **Næste**.
11. Skriv **Firmastrategi** for politiknavnet, og klik derefter på **Næste**.
12. Klik på **Send,** og klik derefter på **Udført**.

Det kan tage noget tid, før **mærkaten Firmastrategi** bliver tilgængelig, når den er publiceret.

Derefter skal du anvende din nye mærkat på **teamet For virksomhedsstrategi** og opdatere standardlinktypen for deling for at reducere risikoen for utilsigtet deling af filer og mapper til en større målgruppe end forventet.

1. Åbn SharePoint Administration under **Websteder**, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
1. Vælg webstedet **Firmastrategi** .
1. Under fanen **Politikker** under **Følsomhed** skal du vælge **Rediger**.
1. Vælg mærkaten **Virksomhedsstrategi** , og vælg derefter **Gem**.
1. Under fanen **Politikker** under **Ekstern deling** skal du vælge **Rediger**.
1. Vælg **Kun personer i din organisation**.
1. Under **Standardlinktype for deling** skal du fjerne markeringen i afkrydsningsfeltet **Samme som indstilling på organisationsniveau** og vælge **Personer med eksisterende adgang**.
1. Vælg **Gem**.

Konfigurer derefter webstedsdeling kun for ejere for **teamet For virksomhedsstrategi** .

1. I Teams skal du gå til fanen **Generelt** i gruppen **Virksomhedsstrategi**.
2. Klik på **Filer** på værktøjslinjen for teamet.
3. Klik på ellipsen, og klik derefter på **Åbn i SharePoint**.
4. Klik på ikonet Indstillinger på værktøjslinjen på det underliggende SharePoint websted, og klik derefter på **Webstedstilladelser**.
5. Klik på **Rediger, hvordan medlemmer kan dele** under **Webstedsdeling** i ruden Webstedstilladelser.
6. Under **Delingstilladelser** skal du vælge **Kun webstedsejere kan dele filer, mapper og webstedet** og derefter klikke på **Gem**.
7. Luk ruderne **Tilladelser** og **Indstillinger**.

Hvis du logger på som medlem af gruppen Virksomhedsstrategi, kan du se **Firmastrategi** i indstillingen **Følsomhed** på værktøjslinjen Hjem i Word, Excel og PowerPoint. Vælg mærkaten **Firmastrategi** i indstillingen **Følsomhed** for at tildele mærkaten til en fil.

Her er den resulterende konfiguration for firmastrategiteamet.

![Konfiguration for det isolerede team for virksomhedsstrategi.](../media/team-security-isolation-dev-test/team-security-isolation-dev-test-config.png)

## <a name="next-step"></a>Næste trin

Når du er klar til produktionsudrulning, skal du se disse [konfigurationsinstruktioner](secure-teams-security-isolation.md).
