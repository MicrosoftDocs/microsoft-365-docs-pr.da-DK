---
title: Registrer og afhjælp godkendelser, som giver samtykke
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Få mere at vide om, hvordan du genkender og afhjælper de tilladelsen, du giver, i Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: db401231a2db0bddf1115cbdf14ae14cc9897f57
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587929"
---
# <a name="detect-and-remediate-illicit-consent-grants"></a>Registrer og afhjælp godkendelser, som giver samtykke

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Oversigt**  Få mere at vide om, hvordan du genkender og afhjælper de tilladelsen, du giver, i Microsoft 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-microsoft-365"></a>Hvad giver det samtykke, som denne giver samtykke, Microsoft 365?

I et usande samtykke giver angreb, opretter hackeren et Azure-registreret program, der anmoder om adgang til data som f.eks. kontaktoplysninger, mail eller dokumenter. Hackeren narrer derefter en slutbruger til at give pågældende program samtykke til at få adgang til deres data enten via et phishingangreb eller ved at indsætte kode, der er tillid til, til et pålideligt websted. Når programmet til uddannelse har fået sit samtykke, har det adgang på kontoniveau til data uden brug af en organisationskonto. Normale afhjælpningstrin, f.eks. nulstilling af adgangskoder for konti, der er brudt, eller krav om multifaktorgodkendelse (MFA) på konti, er ikke effektive mod denne type angreb, da disse er tredjepartsprogrammer og er eksterne i forhold til organisationen.

Disse angreb udnytter en interaktionsmodel, der antager, at den enhed, der kalder oplysningerne, er automatisering og ikke et mennesker.

> [!IMPORTANT]
> Har du mistanke om, at du oplever problemer med samtykkesamtykke fra en app lige nu? Microsoft Defender til skyapps har værktøjer til at registrere, undersøge og afhjælpe dine OAuth-apps. Denne artikel om Defender til skyapps har et selvstudium, der beskriver, hvordan du undersøger [risikobaserede OAuth-apps](/cloud-app-security/investigate-risky-oauth). Du kan også angive [OAuth-apppolitikker](/cloud-app-security/app-permission-policy) for at undersøge tilladelser, som brugerne har anmodet om, og generelt godkende eller forbyde disse anmodninger om tilladelser.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-microsoft-365"></a>Hvordan ser et samtykke til samtykke ud i Microsoft 365?

Du skal søge i **overvågningsloggen for** at finde tegn på dette angreb, også kaldet IOC (Indicators of Compromise). For organisationer med mange Azure-registrerede programmer og en stor brugerbase er den bedste fremgangsmåde at gennemgå dine organisationers samtykkebe givet ugentligt.

### <a name="steps-for-finding-signs-of-this-attack"></a>Trin til at finde tegn på dette angreb

1. Åbn portalen Microsoft 365 Defender, og <https://security.microsoft.com> vælg derefter **Overvågning**. Du kan også gå direkte til siden **Overvågning** ved at bruge <https://security.microsoft.com/auditlogsearch>.

2. Kontrollér **, at** fanen Søg er markeret **på siden** Overvågning, og konfigurer derefter følgende indstillinger:
   - **Dato- og klokkeslætsområde**
   - **Aktiviteter**: Kontrollér, **at Vis resultater for alle aktiviteter** er markeret.

   Når du er færdig, skal du klikke på **Søg**.

3. Klik på **kolonnen** Aktivitet for at sortere resultaterne, og se efter **Samtykke til programmet**.

4. Vælg en post på listen for at få vist detaljerne for aktiviteten. Kontrollér, om IsAdminContent er indstillet til Sand.

> [!NOTE]
>
> Det kan tage fra 30 minutter og op til 24 timer, før den tilsvarende post i overvågningsloggen vises i søgeresultaterne, når en hændelse indtræffer.
>
> Hvor lang tid en overvågningspost opbevares og kan søges i overvågningsloggen, afhænger af dit Microsoft 365-abonnement og specifikt typen af den licens, der er tildelt til en bestemt bruger. Du kan få mere at vide [under Overvågningslog](../../compliance/search-the-audit-log-in-security-and-compliance.md).
>
> Hvis denne værdi er sand, indikerer den, at en person med global administratoradgang kan have givet bred adgang til data. Hvis dette er uventet, skal du følge en vejledning [i at bekræfte et angreb](#how-to-confirm-an-attack).

## <a name="how-to-confirm-an-attack"></a>Sådan bekræftes et angreb

Hvis du har en eller flere forekomster af de IOCs, der er nævnt ovenfor, skal du undersøge yderligere for helt sikkert at bekræfte, at angrebene er sket. Du kan bruge en af disse tre metoder til at bekræfte angrebene:

- Oplagerprogrammer og deres tilladelser ved hjælp Azure Active Directory portalen. Denne metode er grundig, men du kan kun kontrollere én bruger ad gangen, hvilket kan være meget tidskrævende, hvis du har mange brugere, der skal kontrolleres.
- Oplagerprogrammer og deres tilladelser ved hjælp af PowerShell. Dette er den hurtigste og mest omfattende metode med mindst muligt spild.
- Få dine brugere til individuelt at kontrollere deres apps og tilladelser og rapportere resultaterne tilbage til administratorerne for at afhjælpe problemet.

## <a name="inventory-apps-with-access-in-your-organization"></a>Lagerapps med adgang i din organisation

Du kan gøre dette for dine brugere med enten Azure Active Directory-portalen eller PowerShell, eller du kan få dine brugere til selv at optæller deres programadgang.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Trin til brug af Azure Active Directory Portal

Du kan søge efter de programmer, som en enkelt bruger har givet tilladelser til, ved hjælp Azure Active Directory portal på <https://portal.azure.com>.

1. Log på Azure-portalen med administrative rettigheder.
2. Vælg Azure Active Directory bladet.
3. Vælg **Brugere**.
4. Vælg den bruger, du vil gennemse.
5. Vælg **Programmer**.

Dette viser dig de apps, der er tildelt brugeren, og hvilke tilladelser programmerne har.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Trin til at få dine brugere til at optæller deres programadgang

Få dine brugere til at gå til <https://myapps.microsoft.com> og gennemse deres egne programadgang der. De bør kunne se alle apps med adgang, få vist detaljer om dem (herunder adgangsomfanget) og kunne tilbagekalde rettigheder til mistænkelige eller tilsænkne apps.

### <a name="steps-for-doing-this-with-powershell"></a>Trin til at gøre dette med PowerShell

Den nemmeste måde, hvorpå du kan bekræfte det tilladelsesangreb, du får, er at køre [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09), som vil gemme alle OAuth-samtykke-tildelingerne og OAuth-appsene for alle brugere i dit leje i én .csv-fil.

#### <a name="pre-requisites"></a>Forudsætninger

- Azure AD PowerShell-biblioteket er installeret.
- Globale administratorrettigheder for den lejer, som scriptet skal køres op imod.
- Lokal administrator på den computer, som kører scripterne fra.

> [!IMPORTANT]
> Vi ***anbefaler på*** det kraftigste, at du kræver multifaktorgodkendelse på din administrative konto. Dette script understøtter MFA-godkendelse.

1. Log på den computer, som du vil køre scriptet fra med lokale administratorrettigheder.

2. Download eller kopiér [ scriptetGet-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) fra GitHub til en mappe, hvorfra du kører scriptet. Dette er den samme mappe, som outputfilen "permissions.csv" skrives til.

3. Åbn en PowerShell-session som administrator, og åbn den mappe, hvor du gemte scriptet.

4. Forbind til din mappe ved hjælp [af Forbind-AzureAD-cmdlet'en](/powershell/module/azuread/connect-azuread).

5. Kør denne PowerShell-kommando:

   ```powershell
   .\Get-AzureADPSPermissions.ps1 | Export-csv -Path "Permissions.csv" -NoTypeInformation
   ```

Scriptet frembringer én fil med navnet Permissions.csv. Følg disse trin for at søge efter tilladelsestilladelser til programmer:

1. I kolonnen ConsentType (kolonne G) skal du søge efter værdien "AllPrinciples". Tilladelsen AllPrincipals giver klientprogrammet adgang til alles indhold i lejen. Oprindelige Microsoft 365-programmer skal have denne tilladelse for at fungere korrekt. Alle programmer, der ikke er Fra Microsoft, og som har denne tilladelse, skal gennemgås omhyggeligt.

2. Gennemgå de tilladelser, som hvert delegerede program skal have til indhold, i kolonnen Tilladelse (kolonne F). Se efter tilladelsen "Læs" og "Skriv" eller "*. Tilladelsen Alle" og gennemse disse omhyggeligt, da de måske ikke er passende.

3. Gennemse de bestemte brugere, der har givet samtykke. Hvis brugere med høj profil eller høj påvirkning har givet upassende samtykker, bør du undersøge yderligere.

4. Søg efter apps, der virker mistænkelige, i kolonnen ClientDisplayName (kolonne C). Apps med forkert stavede navne, super bland-navne eller hacker-lyde skal gennemses omhyggeligt.

## <a name="determine-the-scope-of-the-attack"></a>Fastlægge omfanget af angrebene

Når du er færdig med at lagerføre programadgang, skal du gennemgå **overvågningsloggen** for at fastlægge det fulde omfang af brudet. Søgning på de berørte brugere, de tidsrammer, som det relevante program havde adgang til din organisation, og de tilladelser, appen havde. Du kan søge i **overvågningsloggen** på [Microsoft 365 Defender portal](../../compliance/search-the-audit-log-in-security-and-compliance.md).

> [!IMPORTANT]
> [Overvågning af postkasse](../../compliance/enable-mailbox-auditing.md) og [aktivitetsrevision for administratorer](../../compliance/turn-audit-log-search-on-or-off.md) og brugere skal være aktiveret før angrebet, for at du kan få disse oplysninger.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant-attack"></a>Sådan stopper og afhjælper du et angreb på et samtykke, der tildeles af dig

Når du har identificeret et program med tilladelser, der giver tilladelser, kan du fjerne adgangen på flere måder.

- Du kan tilbagekalde programmets tilladelse i Azure Active Directory portal ved at:
  1. Gå til den pågældende bruger i **Azure Active Directory Bruger**.
  2. Vælg **Programmer**.
  3. Vælg det program, du vil anvende.
  4. Klik **på Fjern** i detaljeudse detaljeringsruden.

- Du kan tilbagekalde OAuth-samtykket med PowerShell ved at følge trinnene i [Remove-AzureADOAuth2PermissionMissionMission.](/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant)

- Du kan tilbagekalde Tildeling af tjenesteapprolle med PowerShell ved at følge trinnene i [Remove-AzureADServiceAppRoleAssignment](/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment).

- Du kan også deaktivere logon helt for den pågældende konto, hvilket igen deaktiverer appadgang til data i den pågældende konto. Dette er naturligvis ikke ideelt til slutbrugerens produktivitet, men hvis du arbejder på at begrænse effekten hurtigt, kan det være en realistisk løsning på kort sigt.

- Du kan slå integrerede programmer fra for dit leje. Dette er et trin, hvor slutbrugerne ikke kan give samtykke på lejerbasis. Dette forhindrer dine brugere i uforvarende at give adgang til et skadeligt program. Dette anbefales ikke på det kraftigste, da det alvorligt påvirker dine brugeres evne til at være produktive med tredjepartsprogrammer. Det kan du gøre ved at følge trinnene i [Slå integrerede apps til eller fra](../../admin/misc/user-consent.md).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Beskyt Microsoft 365 som en cybersecurity-pro

Dit Microsoft 365-abonnement leveres med et effektivt sæt sikkerhedsfunktioner, som du kan bruge til at beskytte dine data og dine brugere. Brug [Microsoft 365-sikkerhedsoversigten – Topprioriteter for de første 30 dage, 90](security-roadmap.md) dage og derefter for at implementere anbefalede microsoft-fremgangsmåder til sikring af din Microsoft 365 lejer.

- Opgaver, der skal udføres inden for de første 30 dage. Disse har øjeblikkelig indvirkning og har lav effekt for dine brugere.
- Opgaver, der skal udføres på 90 dage. Disse tager lidt mere tid at planlægge og implementere, men i høj grad forbedre din sikkerhed.
- Mere end 90 dage. Disse forbedringer er en del af dit første arbejde på 90 dage.

## <a name="see-also"></a>Se også

- [Uventet program på listen over programmer gennemgår](/azure/active-directory/application-access-unexpected-application) administratorer gennem forskellige handlinger, de måske vil udføre, når de er blevet klar over, at der er uventede programmer med adgang til data.
- [Integrering af programmer Azure Active Directory](/azure/active-directory/active-directory-apps-permissions-consent) er en omfattende oversigt over samtykke og tilladelser.
- [Problemer med at udvikle mit program](/azure/active-directory/active-directory-application-dev-development-content-map) indeholder links til forskellige artikler, der relaterer til samtykke.
- [Program- og tjeneste hovedobjekter i Azure Active Directory (Azure AD)](/azure/active-directory/develop/active-directory-application-objects) giver en oversigt over de program- og tjeneste hovedobjekter, der er centrale for programmodellen.
- [Administrer adgang til apps](/azure/active-directory/active-directory-managing-access-to-apps) er en oversigt over de funktioner, som administratorer skal bruge til at administrere brugeradgang til apps.
