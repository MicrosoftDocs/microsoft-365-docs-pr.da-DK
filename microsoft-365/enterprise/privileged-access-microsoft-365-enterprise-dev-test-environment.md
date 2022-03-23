---
title: Administration af adgang med rettigheder til din Microsoft 365 for Enterprise Test-miljø
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Brug denne Test Lab-vejledning til at aktivere adgangsstyring for Microsoft 365 for virksomhedens testmiljø.
ms.openlocfilehash: 424b7c09a89b20d134654293a1e9c9abd69d6ff2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587653"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Administration af adgang med rettigheder til din Microsoft 365 for Enterprise Test-miljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du konfigurerer adgangsstyring med rettigheder til at øge sikkerheden Microsoft 365 for virksomhedens testmiljø.

Konfiguration af adgangsstyring for privilegeret adgang omfatter tre faser:

- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurer adgangsstyring med rettigheder](#phase-2-configure-privileged-access-management)
- [Fase 3: Kontrollér, at godkendelse er påkrævet for administratoropgaver](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du let vil konfigurere administration af adgangsrettigheder på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere administration af privilegeret adgang i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Test af adgangsstyring med rettigheder kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices skov. Den leveres her som en mulighed, så du kan teste adgangsstyring med rettigheder og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-configure-privileged-access-management"></a>Fase 2: Konfigurer adgangsstyring med rettigheder

I denne fase skal du konfigurere en godkendergruppe og aktivere adgangsstyring for dine Microsoft 365 for virksomhedstestmiljø. Du kan finde flere oplysninger og en oversigt over administration af adgangsrettigheder under [Administration af adgang med rettigheder](../compliance/privileged-access-management-overview.md).

Hvis du vil konfigurere og bruge privilegeret adgang i din organisation, skal du udføre følgende trin.

#### <a name="step-1-create-an-approvers-group"></a>[Trin 1: Opret en godkenders gruppe](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Før du går i gang med at bruge privilegeret adgang, skal du afgøre, hvem der har godkendelsescenteret for indgående anmodninger om adgang til opgaver med administratoradgang og administratoradgang. Alle brugere, der er en del af godkenderens gruppe, kan godkende anmodninger om adgang. Hvis du vil benytte dig af den privilegerede adgang, skal du oprette en mailaktiveret sikkerhedsgruppe Microsoft 365. I testmiljøet skal du navngive den nye sikkerhedsgruppe "Godkendere af adgang med rettigheder" og tilføje "Bruger 3", der tidligere blev oprettet i de tidligere trin i testlaboratoriet.

#### <a name="step-2-enable-privileged-access"></a>[Trin 2: Aktivér adgang med rettigheder](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

Adgang med rettigheder skal udtrykkeligt være slået til i Microsoft 365 med standardgodkendingsgruppen, og den skal indeholde et sæt systemkonti, som skal udelades fra adgangskontrol for adgangsstyringen for den privilegerede adgang. Sørg for at aktivere privilegeret adgang i din organisation, før du starter fase 3 i denne vejledning.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Fase 3: Kontrollér, at godkendelse er påkrævet for administratoropgaver

I denne fase skal du bekræfte, at politikken for privilegeret adgang fungerer, og at brugere kræver godkendelse for at kunne udføre definerede administratoropgaver med administratoradgang og rettigheder.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Test muligheden for at udføre en opgave, DER IKKE er defineret i en politik for adgang med rettigheder

Opret først forbindelse til Exchange Management PowerShell med legitimationsoplysningerne for en bruger, der er konfigureret med rollen Exchange-rollestyring i testmiljøet, og forsøg at oprette en ny journalregel. Opgaven [Ny journalregel er i](/powershell/module/exchange/new-journalrule) øjeblikket ikke defineret i en politik for adgang med rettigheder for organisationen.

1. Åbn og log på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell-modulet** på din lokale computer ved hjælp af legitimationsoplysninger med rollen Exchange-rollestyring for testmiljøet.
2. I Exchange PowerShell skal du oprette en ny journalregel for organisationen:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Se, at den nye journalregel blev oprettet i Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Opret en ny politik for adgang med rettigheder til den New-JournalRule opgave

>[!NOTE]
>Hvis du ikke allerede har fuldført trin 1 og 2 fra fase 2 i denne vejledning, skal du sørge for at følge trinnene for at oprette en godkenders gruppe med navnet "Adgangsgodkendere af rettigheder" for at aktivere privilegeret adgang i dit testmiljø.

1. Log på computeren [Microsoft 365 Administration](https://admin.microsoft.com) legitimationsoplysningerne med Exchange rollestyringsrollen for testmiljøet.
2. I Administration skal du **gå til Indstillinger** >  **Security &** **PrivacyPrivileged** >  Access.
3. Vælg **Administrer adgangspolitikker og -anmodninger**.
4. Vælg **Konfigurer politikker**, og vælg derefter **Tilføj en politik**.
5. Vælg eller angiv følgende værdier fra rullelisten:

    **Politiktype**: Omfang for **opgavepolitik**: Exchange **Policy-navn**: Godkendelsestype for ny **journalregel: Gruppen** Manuel **godkendelse:** Godkendere af adgang med rettigheder  

6. Vælg **Opret**, og vælg derefter **Luk**. Det kan tage et par minutter, før politikken er fuldt konfigureret og aktiveret. Sørg for at give tid til, at politikken kan være fuldt aktiveret, før godkendelseskravet testes i næste trin.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Testgodkendelseskrav for den New-JournalRule opgave, der er defineret i en politik for adgang med rettigheder

1. Åbn og log på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell-modulet** på din lokale computer ved hjælp af legitimationsoplysninger med rollen Exchange-rollestyring for testmiljøet.

2. I Exchange PowerShell skal du oprette en ny journalregel for organisationen:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Få vist fejlen "Utilstrækkelige tilladelser" i Exchange Management PowerShell:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Anmod om adgang til at oprette en ny journalregel ved hjælp New-JournalRule opgaven

1. Log på computeren [Microsoft 365 Administration](https://admin.microsoft.com) legitimationsoplysningerne med Exchange rollestyringsrollen for testmiljøet.

2. I Administration skal du **gå til Indstillinger** >  **Security &** **PrivacyPrivileged** >  Access.

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg **Ny anmodning**. Vælg de relevante værdier for organisationen fra rullelisten:

    **Anmodningstype**: Området **Opgaveanmodning**: Exchange **Request for**: Varighed af ny journalregel **(timer)****: 2 kommentarer**: Anmod om tilladelse til at oprette en ny journalregel  

5. Vælg **Gem**, og vælg derefter **Luk**. Din anmodning sendes til godkenderens gruppe via mail.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Godkend anmodning om adgang med rettigheder til oprettelse af en ny journalregel

1. Log på enheden [Microsoft 365 Administration](https://admin.microsoft.com) legitimationsoplysningerne for Bruger 3 i testmiljøet (medlem af sikkerhedsgruppen "Privilegerede adgangsgodkendere" i testmiljøet).

2. I Administration skal du **gå til Indstillinger** >  **Security &** **PrivacyPrivileged** >  Access.

3. Vælg **Administrer adgangspolitikker og -anmodninger**.

4. Vælg den afventende anmodning, og vælg derefter **Godkend** for at give adgang til brugerkontoen for at oprette en ny journalregel. Kontoen (den anmodende bruger) modtager en mailbekræftelse om, at der er givet godkendelse.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Test, hvor der oprettes en ny journalregel med godkendt adgang til New-JournalRule opgaven

1. Åbn og log på Exchange Online Remote PowerShell-modulet hos **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell-modulet** på din lokale computer ved hjælp af legitimationsoplysninger med rollen Exchange-rollestyring for testmiljøet.

2. I Exchange PowerShell skal du oprette en ny journalregel for organisationen:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Se, at den nye journalregel blev oprettet i Exchange Management PowerShell.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [funktioner til](m365-enterprise-test-lab-guides.md#information-protection) beskyttelse af oplysninger samt funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

- [Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)
- [Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)
- [Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
