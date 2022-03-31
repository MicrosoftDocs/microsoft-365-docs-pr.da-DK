---
title: Brug Azure Privileged Identity Management (PIM) i Microsoft Defender til Office 365 at begrænse administratoradgangen til cybersikkerhedsværktøjer.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 09/03/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Lær at integrere Azure PIM for at give tidsbegrænset, tidsgrænset adgang til brugere til at udføre administratorrettigheder i Microsoft Defender for Office 365, hvilket reducerer risikoen for dine data.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3be90ff1113e25ea418aaf1a25b12574b3bbbe1f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63600958"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM), og hvorfor det skal bruges sammen med Microsoft Defender Office 365

Privileged Identity Management (PIM) er en Azure-funktion, der, når den er konfigureret, giver brugerne adgang til data i en begrænset tidsperiode (nogle gange kaldet tidsinddefinerede tidsperioder), så en bestemt opgave kan udføres. Denne adgang gives "just-in-time" til at udføre den handling, der er påkrævet, og derefter tilbagekaldes. PIM begrænser den adgang og tid, som brugeren har til følsomme data, hvilket reducerer eksponeringsrisici sammenlignet med privilegerede administrationkonti, der har langsigtet adgang til data og andre indstillinger. Så hvordan kan vi bruge denne funktion (PIM) sammen med Microsoft Defender Office 365?

> [!TIP]
> PIM-adgang er begrænset til rolle- og identitetsniveau og gør det muligt at fuldføre flere opgaver. Det må ikke forveksles med styring af adgang med rettigheder (PAM), som er omfattet af et opgaveniveau.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Trin til at bruge PIM til at give just-in-time adgang til Defender for Office 365 relaterede opgaver

Ved at konfigurere PIM til at arbejde sammen med Defender for Office 365 opretter administratorer en proces, som en bruger kan anmode om adgang til for at udføre de nødvendige handlinger. Brugeren skal *begrunde* behovet for udvidelse af sine rettigheder.

I dette eksempel konfigurerer vi "Alex", et medlem af vores sikkerhedsteam, der har stående adgang inden for Office 365, men kan hæve sig til både en rolle, der er påkrævet til almindelige daglige handlinger, f.eks. [Trusselssøgning](threat-hunting-in-threat-explorer.md) og derefter også til et højere rettighedsniveau, når mindre hyppige, men følsomme handlinger, f.eks. afhjælpning af skadelig leveret mail er påkrævet.[](remediate-malicious-email-delivered-office-365.md)

> [!NOTE]
> Dette fører dig gennem de trin, der kræves for at konfigurere PIM til en sikkerhedsanalytiker, der kræver muligheden for at slette mails ved hjælp af Threat Explorer i Microsoft Defender til Office 365, men de samme trin kan bruges til andre RBAC-roller i Sikkerheds- og overholdelsesportalen. Eksempelvis kan denne proces bruges til en informationsmedarbejder, der kræver daglig adgang i eDiscovery for at udføre søgninger og sagsarbejde, men lejlighedsvist har brug for en høj rettighed til at eksportere data fra lejeren.

***Trin 1***. I Azure PIM-konsollen til dit abonnement skal du føje brugeren (Alex) til rollen Azure Security Reader og konfigurere de sikkerhedsindstillinger, der er relateret til aktivering.

1. Log på [Azure AD Administration, og](https://aad.portal.azure.com/) vælg **Azure Active Directory** >  **Roles og administratorer**.
2. Vælg **Sikkerhedslæser** på listen over roller, og vælg **Indstillinger** >  **Edit**
3. Angiv "**Aktiveringens maksimale varighed (timer)**" til en normal arbejdsdag og "Ved aktivering", så der kræves **Azure MFA**.
4. Da dette er Alex' normale rettighedsniveau for daglige handlinger, fjerner vi markeringen Kræv begrundelse for aktivering > **Opdater**.
5. Vælg **Tilføj opgaverNo-medlem** >  **valgt >** vælge eller skrive navnet for at søge efter det rigtige medlem.
6. Klik på  knappen Vælg for at vælge det medlem, du vil føje til PIM-rettigheder > klik på **Næste > foretag** ingen ændringer på siden Tilføj opgave (både tildelingstype Berettiget og varighed  *Permanent* berettiget vil være standard) og **Tildel**.

Navnet på din bruger (her "Alex") vises under Berettigede opgaver på næste side, det betyder, at de kan få vist et PIM i rollen med de indstillinger, der er konfigureret tidligere.

> [!NOTE]
> Du kan få en hurtig gennemgang Privileged Identity Management se [denne video](https://www.youtube.com/watch?v=VQMAg0sa_lE).

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Sørg for at scanne indstillingerne for rollen Sikkerhedslæser i Administration af adgang med rettigheder. Her kan du se, at PIM-aktiveringens maksimale varighed er 8 timer.":::

***Trin 2***. Opret den nødvendige anden (administratorrettigheder) tilladelsesgruppe for yderligere opgaver, og tildel berettigelse.

Med [grupper med adgangstilladelser](/azure/active-directory/privileged-identity-management/groups-features) kan vi nu oprette vores egne brugerdefinerede grupper og kombinere tilladelser eller øge granulariteten, hvor det er nødvendigt, så de opfylder dine forretningsmetoder og behov.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Opret en rollegruppe, der kræver de nødvendige tilladelser

I portalen Microsoft 365 Defender du oprette en brugerdefineret rollegruppe, der indeholder de tilladelser, vi ønsker.

1. I portalen Microsoft 365 Defender skal du <https://security.microsoft.com>gå til **Tilladelser & Roller** og derefter vælge **Roller** under **Mail og samarbejde**. For at gå direkte til **siden Tilladelser skal** du bruge <https://security.microsoft.com/emailandcollabpermissions>.
2. Klik **på ikonet Opret** på ![siden Tilladelser.](../../media/m365-cc-sc-create-icon.png) **Opret**.
3. Navngive din gruppe for at afspejle dens formål, f.eks. "Søg og Tøm PIM".
4. Tilføj ikke medlemmer, gem blot gruppen, og gå videre til næste del!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Opret sikkerhedsgruppen i Azure AD for administratorrettigheder

1. Gå tilbage til [Azure AD Administration, og](https://aad.portal.azure.com/) gå til **Azure** **ADGroupsNew** >  >  **Group**.
2. Navngive din Azure AD-gruppe for at afspejle dens formål. **I øjeblikket kræves der ingen ejere eller** medlemmer.
3. Gør **Azure AD-roller til kan tildeles til gruppen** til **Ja**.
4. Tilføj ikke nogen roller, medlemmer eller ejere, opret gruppen.
5. Gå tilbage til den gruppe, du lige har oprettet, og vælg **Privileged AccessEnable** >  **Privileged Access**.
6. Inden for gruppen skal du vælge Berettigede opgaverFæl tildelinger **> Tilføj** den bruger,  >  der skal bruge & Tøm **som medlem.**
7. Konfigurer indstillingerne **Indstillinger** gruppens Adgangspriviligerede adgang. Vælg **Rediger** indstillingerne for rollen **medlem**.
8. Du kan ændre aktiveringstiden, så det passer til din organisation. I dette eksempel kræves *Azure MFA*, *begrundelse* og *oplysninger om billet,* før du vælger **Opdater**.

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Indlejr den nyoprettede sikkerhedsgruppe i rollegruppen

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell), og kør følgende kommando:

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Test din konfiguration af PIM med Defender for Office 365

1. Log på med testbrugeren (Alex), som på nuværende tidspunkt ikke skal have [administratoradgang Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center) portalen.
2. Gå til PIM, hvor brugeren kan aktivere deres daglige sikkerhedslæserrolle.
3. Hvis du forsøger at fjerne en mail ved hjælp af Threat Explorer, får du en fejl om, at du skal bruge yderligere tilladelser.
4. PIM en gang til i den mere hævede rolle bør du efter en kort forsinkelse nu kunne fjerne mails uden problemer.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Hvis den bruger, vi har tilføjet (Alex) via sikkerhedslæserens PIM-rolle, forsøger at slette en mistænkelig mail, får han vist en meddelelse, hvor der står: &quot;Du skal bruge rollen Søg og Tøm for at kunne handle på denne mail. Kontakt din administrator for at få rolletildelingen eller føje mailen til en hændelse.":::

Permanent tildeling af administrative roller og tilladelser som f.eks. Søg og Tøm rolle indeholder ikke nultillidssikkerhedsinitiativet, men som du kan se, kan PIM bruges til at give just-in-time adgang til det påkrævede værktøjssæt.

*Tak til kundeteknikeren Ben Harris for at få adgang til blogindlægget og de ressourcer, der bruges til dette indhold.*

<!--A-->