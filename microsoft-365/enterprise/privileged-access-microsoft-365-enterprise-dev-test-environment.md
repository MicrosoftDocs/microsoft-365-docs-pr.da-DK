---
title: Privilegeret adgangsstyring for dit Microsoft 365 til virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Brug denne testlaboratorievejledning til at aktivere privilegeret adgangsstyring af dine Microsoft 365 til virksomhedstestmiljøer.
ms.openlocfilehash: 0c92cbd398e4c388fe3c5999c5e0aa9973c4ee06
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092089"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Privilegeret adgangsstyring for dit Microsoft 365 til virksomhedstestmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du konfigurerer privilegeret adgangsstyring for at øge sikkerheden i dit Microsoft 365 til virksomhedstestmiljøer.

Konfiguration af privilegeret adgangsstyring omfatter tre faser:

- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurer privilegeret adgangsstyring](#phase-2-configure-privileged-access-management)
- [Fase 3: Kontrollér, at godkendelse er påkrævet til øgede og privilegerede opgaver](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du vil konfigurere privilegeret adgangsstyring på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af Letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere privilegeret adgangsstyring i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Test af privilegeret adgangsstyring kræver ikke det simulerede testmiljø for virksomheder, hvilket omfatter et simuleret intranet, der er forbundet til internet- og mappesynkronisering for et Active Directory-domæneservices område. Den leveres her som en mulighed, så du kan teste privilegeret adgangsstyring og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-configure-privileged-access-management"></a>Fase 2: Konfigurer privilegeret adgangsstyring

I denne fase skal du konfigurere en godkendergruppe og aktivere privilegeret adgangsstyring for dit Microsoft 365 til virksomhedstestmiljø. Du kan finde flere oplysninger og en oversigt over administration af privilegeret adgang under [Privilegeret adgangsstyring](../compliance/privileged-access-management-overview.md).

Udfør følgende trin for at konfigurere og bruge privilegeret adgang i din organisation.

#### <a name="step-1-create-an-approvers-group"></a>[Trin 1: Opret en godkenders gruppe](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Før du begynder at bruge privilegeret adgang, skal du bestemme, hvem der har godkendelsestilladelse til indgående anmodninger om adgang til udvidede og privilegerede opgaver. Alle brugere, der er en del af godkendergruppen, kan godkende anmodninger om adgang. Hvis du vil bruge privilegeret adgang, skal du oprette en mailaktiveret sikkerhedsgruppe i Microsoft 365. I dit testmiljø skal du navngive den nye sikkerhedsgruppe "Privilegerede adgangsgodkendere" og tilføje "Bruger 3", der tidligere blev oprettet i tidligere trin i vejledningen til testlaboratoriet.

#### <a name="step-2-enable-privileged-access"></a>[Trin 2: Aktivér privilegeret adgang](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

Privilegeret adgang skal være udtrykkeligt aktiveret i Microsoft 365 med standardgodkendergruppen, og den skal indeholde et sæt systemkonti, som du vil udelade fra den privilegerede adgangsstyring. Sørg for at aktivere privilegeret adgang i din organisation, før du starter fase 3 i denne vejledning.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Fase 3: Kontrollér, at godkendelse er påkrævet til øgede og privilegerede opgaver

I denne fase skal du kontrollere, at politikken for privilegeret adgang fungerer, og at brugerne skal godkende for at udføre definerede udvidede og privilegerede opgaver.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Test muligheden for at udføre en opgave, der IKKE er defineret i en privilegeret adgangspolitik

Først skal du oprette forbindelse til Exchange Management PowerShell med legitimationsoplysningerne for en bruger, der er konfigureret med rollen Exchange rolleadministration i testmiljøet, og forsøge at oprette en ny journalregel. Opgaven [Ny-JournalRule](/powershell/module/exchange/new-journalrule) er i øjeblikket ikke defineret i en politik for privilegeret adgang for din organisation.

1. På din lokale computer skal du åbne og logge på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** ved hjælp af legitimationsoplysninger med rollen Exchange rolleadministration for dit testmiljø.
2. I Exchange administration af PowerShell skal du oprette en ny journalregel for din organisation:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Vis, at den nye journalregel blev oprettet i PowerShell Exchange administration.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Opret en ny privilegeret adgangspolitik for den New-JournalRule opgave

>[!NOTE]
>Hvis du ikke allerede har fuldført trin 1 og 2 fra fase 2 i denne vejledning, skal du sørge for at følge trinnene for at oprette en godkenders gruppe med navnet "Rettighedsadgangsgodkendere" for at aktivere privilegeret adgang i dit testmiljø.

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger med rollen Exchange rolleadministration for dit testmiljø.
2. I Administration skal du gå til **Indstillinger** >  **Sikkerhed & Beskyttelse af personlige** **oplysningerPrivilegeret** >  adgang.
3. Vælg **Administrer adgangspolitikker og -anmodninger**.
4. Vælg **Konfigurer politikker**, og vælg derefter **Tilføj en politik**.
5. På rullelisten skal du vælge eller angive følgende værdier:

    **Politiktype**: **Opgavepolitikområde**: Exchange **Politiknavn**: Ny **godkendelsestype** for journalregel: Manuel **godkendelsesgruppe**: Privilegerede adgangsgodkendere  

6. Vælg **Opret**, og vælg derefter **Luk**. Det kan tage et par minutter, før politikken er fuldt konfigureret og aktiveret. Sørg for at give politikken tid til at være fuldt aktiveret, før du tester godkendelseskravet i næste trin.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Test godkendelseskrav for den New-JournalRule opgave, der er defineret i en politik for privilegeret adgang

1. På din lokale computer skal du åbne og logge på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** ved hjælp af legitimationsoplysninger med rollen Exchange rolleadministration for dit testmiljø.

2. I Exchange administration af PowerShell skal du oprette en ny journalregel for din organisation:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Vis fejlen "Utilstrækkelige tilladelser" i Exchange Management PowerShell:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Anmod om adgang for at oprette en ny journalregel ved hjælp af New-JournalRule opgave

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af legitimationsoplysninger med rollen Exchange rolleadministration for dit testmiljø.

2. I Administration skal du gå til **Indstillinger** >  **Sikkerhed & Beskyttelse af personlige** **oplysningerPrivilegeret** >  adgang.

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Ny anmodning**. Vælg de relevante værdier for din organisation på rullelisten:

    **Anmodningstype**: **Område for opgaveanmodning**: Exchange **Anmodning om**: Varighed af ny journalregel **(timer)**: 2 **kommentarer**: Anmodningstilladelser til at oprette en ny journalregel  

5. Vælg **Gem**, og vælg derefter **Luk**. Din anmodning sendes til godkenderens gruppe via mail.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Godkend anmodning om privilegeret adgang til oprettelse af en ny journalregel

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af legitimationsoplysningerne for Bruger 3 i testmiljøet (medlem af sikkerhedsgruppen "Privilegerede adgangsgodkendere" i testmiljøet).

2. I Administration skal du gå til **Indstillinger** >  **Sikkerhed & Beskyttelse af personlige** **oplysningerPrivilegeret** >  adgang.

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg den ventende anmodning, og vælg derefter **Godkend** for at give adgang til brugerkontoen for at oprette en ny journalregel. Kontoen (den anmodende bruger) modtager en mailbekræftelse om, at godkendelsen blev tildelt.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Test oprettelse af en ny journalregel med privilegeret adgang godkendt for den New-JournalRule opgave

1. På din lokale computer skal du åbne og logge på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** ved hjælp af legitimationsoplysninger med rollen Exchange rolleadministration for dit testmiljø.

2. I Exchange administration af PowerShell skal du oprette en ny journalregel for din organisation:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Vis, at den nye journalregel blev oprettet i PowerShell Exchange administration.

## <a name="next-step"></a>Næste trin

Udforsk yderligere funktioner og funktioner til [beskyttelse af oplysninger](m365-enterprise-test-lab-guides.md#information-protection) i dit testmiljø.

## <a name="see-also"></a>Se også

- [vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)
- [Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)
- [Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
