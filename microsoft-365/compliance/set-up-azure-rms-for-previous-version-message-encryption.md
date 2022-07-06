---
title: Konfigurer Azure Rights Management til den tidligere version af meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/30/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 2cba47b3-f09e-4911-9207-ac056fcb9db7
description: Den tidligere version af Office 365 Meddelelseskryptering afhænger af Microsoft Azure Rights Management (tidligere kendt som Windows Azure Active Directory Rights Management).
ms.openlocfilehash: 386056c282ea5f4ad996cc7ae7c50926436fe720
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641356"
---
# <a name="set-up-azure-rights-management-for-the-previous-version-of-message-encryption"></a>Konfigurer Azure Rights Management til den tidligere version af meddelelseskryptering

I dette emne beskrives de trin, du skal følge for at aktivere og derefter konfigurere Azure Rights Management (RMS), der er en del af Azure Information Protection, til brug med den tidligere version af Office 365 Message Encryption (OME).

## <a name="this-article-only-applies-to-the-previous-version-of-ome"></a>Denne artikel gælder kun for den tidligere version af OME

Hvis du endnu ikke har flyttet din organisation til Microsoft Purview-meddelelseskryptering, men du allerede har installeret OME, gælder oplysningerne i denne artikel for din organisation. Microsoft anbefaler, at du planlægger at flytte til Microsoft Purview-meddelelseskryptering, så snart det er rimeligt for din organisation. Du kan finde en vejledning under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan de nye funktioner fungerer først, skal du se [Meddelelseskryptering](ome.md). Resten af denne artikel refererer til OME-funktionsmåde før udgivelsen af Microsoft Purview-meddelelseskryptering.

## <a name="prerequisites-for-using-the-previous-version-of-office-365-message-encryption"></a>Forudsætninger for brug af den tidligere version af Office 365 meddelelseskryptering
<a name="warmprereqs"> </a>

Office 365 OME (Message Encryption), herunder IRM, afhænger af Azure Rights Management (Azure RMS). Azure RMS er den beskyttelsesteknologi, der bruges af Azure Information Protection. Hvis du vil bruge OME, skal din organisation inkludere et Exchange Online- eller Exchange Online Protection-abonnement, der igen omfatter et Azure Rights Management-abonnement.

- Hvis du ikke er sikker på, hvad dit abonnement omfatter, kan du se tjenestebeskrivelserne for Exchange Online for [Meddelelsespolitik, Genoprettelse og Overholdelse af angivne standarder](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

- Hvis du har Azure Rights Management, men den ikke er konfigureret til Exchange Online eller Exchange Online Protection, forklares det i denne artikel, hvordan du aktiverer Azure Rights Management, og derefter beskrives den bedste måde at konfigurere OME til at arbejde med Azure Rights Management på.

- Hvis du allerede har konfigureret OME til at arbejde med Azure Rights Management til Exchange Online eller Exchange Online Protection, kan du være klar til at begynde at bruge OME og de nye funktioner med det samme, afhængigt af hvordan du konfigurerer det. I denne artikel forklares det, hvordan du afgør, om du har konfigureret OME korrekt, hvad du skal gøre, hvis du har brug for at ændre konfigurationen, og hvad der sker, hvis du vælger ikke at ændre konfigurationen. Hvis du f.eks. vil bruge de nye funktioner, skal du bruge Azure RMS med OME. Du kan ikke bruge de nye funktioner sammen med en Active Directory i det lokale miljø RMS.

## <a name="activate-azure-rights-management-for--the-previous-version-of-ome-in-office-365"></a>Aktivér Azure Rights Management for den tidligere version af OME i Office 365

Du skal aktivere Azure Rights Management, så brugerne i din organisation kan anvende information protection på meddelelser, de sender, og åbne meddelelser og filer, der er beskyttet af Tjenesten Azure Rights Management. Du kan finde instruktioner under [Aktivering af Azure Rights Management](/azure/information-protection/activate-service). Når du har fuldført aktiveringen, skal du vende tilbage hertil og fortsætte med opgaverne i denne artikel.

## <a name="set-up-the-previous-version-of-ome-to-use-azure-rms-by-importing-trusted-publishing-domains-tpds"></a>Konfigurer den tidligere version af OME for at bruge Azure RMS ved at importere TPD'er (publiceringsdomæner, der er tillid til)

En TPD er en XML-fil, der indeholder oplysninger om organisationens indstillinger for administration af rettigheder. TPD indeholder f.eks. oplysninger om det SLC-certifikat (Server Licensor Certificate), der bruges til at signere og kryptere certifikater og licenser, de URL-adresser, der bruges til licensering og publicering osv. Du importerer TPD til din organisation ved hjælp af PowerShell.

> [!IMPORTANT]
> Tidligere kunne du vælge at importere TPD'er fra AD RMS (Active Directory Rights Management Service) til din organisation. Hvis du gør det, vil det dog forhindre dig i at bruge Microsoft Purview-meddelelseskryptering og anbefales ikke. Hvis din organisation i øjeblikket er konfigureret på denne måde, anbefaler Microsoft, at du opretter en plan for migrering fra din Active Directory i det lokale miljø RMS til cloudbaseret Azure-Information Protection. Du kan få flere oplysninger under [Overførsel fra AD RMS til Azure Information Protection](/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms). Du kan ikke bruge Microsoft Purview-meddelelseskryptering, før du har fuldført migreringen til Azure Information Protection.

**Sådan importerer du TPD'er fra Azure RMS**:

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Vælg den URL-adresse til nøgledeling, der svarer til din organisations geografiske placering:

   |Placering|URL-adresse til placering af nøgledeling|
   |---|---|
   |Nordamerika|<https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Eu|<https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Asien|<https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Sydamerika|<https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc>|
   |Office 365 til offentlige myndigheder (Government Community Cloud)  <br/> Denne RMS-nøgledelingsplacering er reserveret til kunder, der har købt Office 365 til offentlige SKU'er.|<https://sp-rms.govus.aadrm.com/TenantManagement/ServicePartner.svc>|

3. Konfigurer placeringen for nøgledeling ved at køre [Set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "<RMSKeySharingURL >"
   ```

   Hvis du f.eks. vil konfigurere placeringen af nøgledeling, hvis din organisation er placeret i Nordamerika:

   ```powershell
   Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
   ```

4. Kør [Cmdlet'en Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain) med parameteren -RMSOnline for at importere TPD fra Azure Rights Management:

   ```powershell
   Import-RMSTrustedPublishingDomain -RMSOnline -Name "<TPDName> "
   ```

   Hvor  *TPDName*  er det navn, du vil bruge til TPD. For eksempel "Contoso nordamerikansk TPD".

5. Hvis du vil bekræfte, at du har konfigureret din organisation til at bruge Azure Rights Management-tjenesten, skal du køre cmdlet'en [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration) med parameteren -RMSOnline på følgende måde:

   ```powershell
   Test-IRMConfiguration -RMSOnline
   ```

   Denne cmdlet kontrollerer bl.a. forbindelsen til Azure Rights Management-tjenesten, downloader TPD og kontrollerer dens gyldighed.

6. Kør [Set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde for at deaktivere Azure Rights Management-skabeloner, så de ikke er tilgængelige i Outlook på internettet og Outlook:

   ```powershell
   Set-IRMConfiguration -ClientAccessServerEnabled $false
   ```

7. Kør [Set-IRMConfiguration-cmdlet'en](/powershell/module/exchange/set-irmconfiguration) på følgende måde for at aktivere Azure Rights Management for din skybaserede mailorganisation og konfigurere den til at bruge Azure Rights Management til Office 365 meddelelseskryptering:

   ```powershell
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```

8. Hvis du vil kontrollere, at du har importeret TPD og aktiveret Azure Rights Management, skal du bruge cmdlet'en Test-IRMConfiguration til at teste Azure Rights Management-funktionalitet. Du kan finde flere oplysninger under "Eksempel 1" i [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

## <a name="i-have-the-previous-version-of-ome-set-up-with-active-directory-rights-management-not-azure-information-protection-what-do-i-do"></a>Jeg har den tidligere version af OME konfigureret med Active Directory Rights Management, ikke Azure Information Protection. Hvad gør jeg?
<a name="importTPDs"> </a>

Du kan fortsætte med at bruge dine eksisterende Office 365 regler for mailkryptering af meddelelser med Active Directory Rights Management, men du kan ikke konfigurere eller bruge Microsoft Purview-meddelelseskryptering. Du skal i stedet migrere til Azure Information Protection. Du kan få oplysninger om migrering, og hvad det betyder for din organisation, under [Overførsel fra AD RMS til Azure Information Protection](/information-protection/deploy-use/prepare-environment-adrms).

## <a name="next-steps"></a>Næste trin
<a name="importTPDs"> </a>

Når du har fuldført konfigurationen af Azure Rights Management, kan du se [Konfigurer Microsoft Purview-meddelelseskryptering](./set-up-new-message-encryption-capabilities.md), hvis du vil aktivere Microsoft Purview-meddelelseskryptering.

Når du har konfigureret din organisation til at bruge Microsoft Purview-meddelelseskryptering, er du klar til at [definere regler for mailflow](define-mail-flow-rules-to-encrypt-email.md).

## <a name="related-topics"></a>Relaterede emner
<a name="importTPDs"> </a>

[Kryptering i Office 365](encryption.md)

[Tekniske referenceoplysninger om kryptering i Office 365](technical-reference-details-about-encryption.md)

[Hvad er Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)
