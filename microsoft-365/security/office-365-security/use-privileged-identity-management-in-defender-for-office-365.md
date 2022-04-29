---
title: Brug Azure Privileged Identity Management (PIM) i Microsoft Defender for Office 365 til at begrænse administratoradgang til værktøjer til cybersikkerhed.
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
description: Få mere at vide om, hvordan du integrerer Azure PIM for at tildele just-in-time, tidsbegrænset adgang til brugere til at udføre opgaver med øgede rettigheder i Microsoft Defender for Office 365, så risikoen for dine data reduceres.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6e043a671b2416ba1c856c74a53206b06c180f13
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130664"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management (PIM), og hvorfor du skal bruge den sammen med Microsoft Defender for Office 365

Privileged Identity Management (PIM) er en Azure-funktion, der, når den er konfigureret, giver brugerne adgang til data i en begrænset periode (også kaldet tidsrammet tidsperiode), så en bestemt opgave kan udføres. Denne adgang gives "just-in-time" til at udføre den handling, der kræves, og derefter tilbagekaldt. PIM begrænser den adgang og tid, som brugeren har til følsomme data, hvilket reducerer eksponeringsrisikoen sammenlignet med privilegerede administrationskonti, der har langsigtet adgang til data og andre indstillinger. Så hvordan kan vi bruge denne funktion (PIM) sammen med Microsoft Defender for Office 365?

> [!TIP]
> PIM-adgang er begrænset til rolle- og identitetsniveauet og tillader fuldførelse af flere opgaver. Det er ikke at forveksle med PAM (Privileged Access Management), som er begrænset på opgaveniveau.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>Trin til at bruge PIM til at give just-in-time-adgang til Defender for Office 365 relaterede opgaver

Ved at konfigurere PIM til at arbejde med Defender for Office 365 opretter administratorer en proces, hvor en bruger kan anmode om adgang til at udføre de handlinger, de har brug for. Brugeren skal *begrunde* behovet for udvidede rettigheder.

I dette eksempel konfigurerer vi "Alex", der er medlem af vores sikkerhedsteam, og som har nul stående adgang inden for Office 365, men som både kan løfte den rolle, der kræves til normale daglige handlinger, f.eks[. Threat Hunting](threat-hunting-in-threat-explorer.md), og derefter til et højere niveau af rettigheder, når mindre hyppige, men følsomme handlinger, f.eks. [afhjælpning af ondsindet leveret mail](remediate-malicious-email-delivered-office-365.md) er påkrævet.

> [!NOTE]
> Dette fører dig gennem de trin, der kræves for at konfigurere PIM for en sikkerhedsanalytiker, der kræver muligheden for at fjerne mails ved hjælp af Threat Explorer i Microsoft Defender for Office 365, men de samme trin kan bruges til andre RBAC-roller på portalen Sikkerhed og Overholdelse. Denne proces kan f.eks. bruges til en informationsmedarbejder, der kræver dag-til-dag-adgang i eDiscovery for at udføre søgninger og sagsarbejde, men som kun lejlighedsvis har brug for den øgede ret til at eksportere data fra lejeren.

***Trin 1***. I Azure PIM-konsollen for dit abonnement skal du føje brugeren (Alex) til rollen Azure Security Reader og konfigurere de sikkerhedsindstillinger, der er relateret til aktivering.

1. Log på [Azure AD Administration](https://aad.portal.azure.com/), og vælg **Azure Active Directory** >  **Rolles og administratorer**.
2. Vælg **Sikkerhedslæser** på listen over roller, og **Indstillinger** >  **Derefter Rediger**
3. Angiv '**Maksimal aktiveringsvarighed (timer)**' til en normal arbejdsdag og 'Ved aktivering' for at kræve **Azure MFA**.
4. Da dette er Alex' normale rettighedsniveau for daglige handlinger, fjerner vi markeringen **af Kræv berettigelse ved aktivering**' > **opdatering**.
5. Vælg **Tilføj tildelingerDet** >  **er ikke valgt et medlem** > vælge eller skrive navnet for at søge efter det korrekte medlem.
6. Klik på knappen **Vælg** for at vælge det medlem, du vil tilføje for PIM-rettigheder, > klik på **Næste** > ikke foretage ændringer på siden Tilføj tildeling (både tildelingstype *Berettiget* og varighed *Permanent berettiget* vil være standard) og **Tildel**.

Navnet på din bruger (her 'Alex') vises under Berettigede tildelinger på næste side. Det betyder, at brugeren kan bruge PIM til rollen med de indstillinger, der er konfigureret tidligere.

> [!NOTE]
> Du kan få en hurtig gennemgang af Privileged Identity Management i [denne video](https://www.youtube.com/watch?v=VQMAg0sa_lE).

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Oplysninger om rolleindstilling – siden Sikkerhedslæser" lightbox="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png":::

***Trin 2***. Opret den nødvendige anden tilladelsesgruppe (med administratorrettigheder) til yderligere opgaver, og tildel berettigelse.

Ved hjælp af [privilegerede adgangsgrupper](/azure/active-directory/privileged-identity-management/groups-features) kan vi nu oprette vores egne brugerdefinerede grupper og kombinere tilladelser eller øge granulariteten, hvor det er nødvendigt for at opfylde dine organisatoriske fremgangsmåder og behov.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Opret en rollegruppe, der kræver de tilladelser, vi har brug for

Opret en brugerdefineret rollegruppe, der indeholder de ønskede tilladelser, i Microsoft 365 Defender-portalen.

1. Gå til **Tilladelser & Roller** i Microsoft 365 Defender-portalen på <https://security.microsoft.com>, og vælg derefter **Roller** under **Mail og samarbejde**. Hvis du vil gå direkte til siden **Tilladelser** , skal du bruge <https://security.microsoft.com/emailandcollabpermissions>.
2. Klik på Ikonet Opret på ![siden **Tilladelser**.](../../media/m365-cc-sc-create-icon.png) **Opret**.
3. Navngiv din gruppe, så den afspejler dens formål, f.eks. 'Søg og Fjern PIM'.
4. Tilføj ikke medlemmer, du skal blot gemme gruppen og gå videre til næste del!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Opret sikkerhedsgruppen i Azure AD for administratorrettigheder

1. Gå tilbage til [Azure AD Administration](https://aad.portal.azure.com/), og naviger til **Azure AD** >  **GroupsNew** >  **Group**.
2. Navngiv din Azure AD gruppe, så den afspejler formålet. Der **kræves ingen ejere eller medlemmer** lige nu.
3. Slå **Azure AD roller kan tildeles til gruppen** til **Ja**.
4. Tilføj ikke nogen roller, medlemmer eller ejere, opret gruppen.
5. Gå tilbage til den gruppe, du lige har oprettet, og vælg **Privilegeret adgang** >  **Privilegeret adgang.**
6. I gruppen skal du vælge **Berettigede tildelingerTilføj** >  **tildelinger** > Tilføj den bruger, der skal bruge Søg & Fjern som **medlem.**
7. Konfigurer **Indstillinger** i gruppens rude Privilegeret adgang. Vælg at **redigere** indstillingerne for **rollen medlem**.
8. Skift aktiveringstiden, så den passer til din organisation. I dette eksempel kræves *der oplysninger om* *Azure MFA*, *begrundelse* og billet, før du vælger **Opdater**.

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Indlejrer den nyoprettede sikkerhedsgruppe i rollegruppen

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell), og kør følgende kommando:

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>Test din konfiguration af PIM med Defender for Office 365

1. Log på med testbrugeren (Alex), som på nuværende tidspunkt ikke skal have administrativ adgang på [Microsoft 365 Defender-portalen](/microsoft-365/security/defender/overview-security-center).
2. Gå til PIM, hvor brugeren kan aktivere sin daglige sikkerhedslæserrolle.
3. Hvis du forsøger at fjerne en mail ved hjælp af Threat Explorer, får du vist en fejl, der angiver, at du skal have yderligere tilladelser.
4. PIM en anden gang i den mere forhøjede rolle, efter en kort forsinkelse bør du nu være i stand til at rense e-mails uden problem.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Ruden Handlinger under fanen Mail" lightbox="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG":::

Permanent tildeling af administrative roller og tilladelser, f.eks. rollen Søg og Fjern, er ikke i overensstemmelse med Nul tillid sikkerhedsinitiativ, men som du kan se, kan PIM bruges til at give just-in-time-adgang til det krævede værktøjssæt.

*Vores tak til Kundetekniker Ben Harris for adgang til blogindlægget og ressourcer, der bruges til dette indhold.*

<!--A-->
