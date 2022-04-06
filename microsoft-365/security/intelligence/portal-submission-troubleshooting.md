---
title: Fejlfinding af MSI-portalfejl forårsaget af administratorblok
description: Fejlfinding af MSI-portalfejl
ms.reviewer: ''
keywords: sikkerhed, hjælp til eksempel på indsendelse, malwarefil, virusfil, trojansk fil, indsend, send til Microsoft, send en prøve, virus, trojansk, orm, ikke registreres, mail microsoft, mailmalware, jeg tror, dette er malware, jeg tror, det er en virus, hvor kan jeg sende en virus, er dette en virus, MSE, kan ikke registrere, ingen signatur, ingen registrering, mistænkelig fil,  MMPC, Microsoft Malware Protection Center, forsker, analytiker, WDSI, sikkerhedsintelligens
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: e70eb5192a1fd6171b8e515509ad336aa99a2c63
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705775"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Fejlfinding i forbindelse med malwareindsendelsesfejl forårsaget af administratorblokering
I nogle tilfælde kan en administratorblokering give problemer med indsendelsen, når du forsøger at indsende en potentielt inficeret fil til [Microsoft Security Intelligence-webstedet](https://www.microsoft.com/wdsi) til analyse. Følgende proces viser, hvordan du løser dette problem.

## <a name="review-your-settings"></a>Gennemse dine indstillinger
Åbn indstillingerne for dit Azure [Enterprise-program](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). Under **Enterprise ApplicationsUsers** >   **kan give samtykke til, at apps får adgang til virksomhedsdata** på deres vegne skal du kontrollere, om Ja eller Nej er markeret.

- Hvis **Nej** er valgt, skal en Azure AD-administrator for kundelejeren give samtykke for organisationen. Afhængigt af konfigurationen med Azure AD kan brugerne muligvis sende en anmodning direkte fra den samme dialogboks. Hvis der ikke er nogen mulighed for at anmode om administratorsamtykke, skal brugerne anmode om, at disse tilladelser føjes til deres Azure AD-administrator. Gå til det følgende afsnit for at få mere at vide.

- Hvis **Ja** er markeret, skal du sikre dig, Windows Defender Security Intelligence-appindstillingen **Aktiveret for brugere til** at logge på? er **indstillet til** [Ja i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).Hvis **Nej** er valgt, skal du anmode en Azure AD-administrator om at aktivere det. 
  
## <a name="implement-required-enterprise-application-permissions"></a>Implementer påkrævede virksomhedsprogramtilladelser 
Denne proces kræver en global administrator eller en programadministrator i lejeren.
 1. Åbn [indstillinger for virksomhedsprogram](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). 
 2. Vælg **Giv administratorsamtykke for organisationen**.
 3. Hvis du kan gøre dette, skal du gennemgå de API-tilladelser, der kræves til dette program, som følgende billede viser. Giv samtykke for lejeren.

    ![billede, der giver samtykke.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

  4. Hvis administratoren modtager en fejl under forsøget på at give samtykke manuelt, kan du prøve enten mulighed [1](#option-1-approve-enterprise-application-permissions-by-user-request) eller [mulighed 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) som mulige løsninger.
  
## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Mulighed 1 Godkend tilladelser for virksomhedsprogram efter brugeranmodning
> [!Note]
> Dette er i øjeblikket en eksempelfunktion.

Azure Active Directory administratorer skal give brugerne mulighed for at anmode om administratorsamtykke til apps. Kontrollér, at indstillingen er konfigureret til **Ja** i [Enterprise-programmer](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Brugerindstillinger for virksomhedsprogrammer.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Du kan finde flere oplysninger i Konfigurere [arbejdsproces for administratorsamtykke](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Når denne indstilling er bekræftet, kan brugerne gå gennem virksomhedens kundeadgang til [Microsoft-sikkerhedsintelligens](https://www.microsoft.com/wdsi/filesubmission) og sende en anmodning om administratorsamtykke, herunder begrundelse.

![Contoso-logonflow.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Administratoren vil kunne gennemse og godkende programtilladelserne for [Azure-administratorsamtykke](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

Når du har givet dit samtykke, vil alle brugere i lejeren kunne bruge programmet.
  
## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Mulighed 2 Giv administratorsamtykke ved at godkende programmet som administrator 
Denne proces kræver, at globale administratorer gennemgår Enterprise-kunde-logonflowet hos [Microsoft-sikkerhedsintelligens](https://www.microsoft.com/wdsi/filesubmission).

![Flow for samtykke til logon.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Derefter gennemser administratorer tilladelserne, sørger for at vælge **Samtykke på vegne af din organisation** og vælger derefter **Acceptér**.

Alle brugere i lejeren vil nu kunne bruge dette program.

## <a name="option-3-delete-and-readd-app-permissions"></a>Mulighed 3: Slette og læse app-tilladelser
Hvis ingen af disse indstillinger løser problemet, kan du prøve følgende trin (som administrator):

1. Fjern tidligere konfigurationer for programmet. Gå til [Virksomhedsprogrammer,](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) og vælg **Slet**.

   ![Slet apptilladelser.](../../media/security-intelligence-images/msi-properties.png)

2. Registrer TenantID fra [Egenskaber](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Erstat {tenant-id} med den specifikke lejer, der skal give samtykke til dette program i URL-adressen nedenfor. Kopiér denne URL-adresse til browseren. Resten af parametrene er allerede fuldført. 
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Der kræves tilladelser.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Gennemse de tilladelser, der kræves af programmet, og vælg derefter **Acceptér**. 

5. Bekræft, at tilladelserne anvendes i [Azure-portalen](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Gennemse, at tilladelserne er anvendt.](../../media/security-intelligence-images/msi-permissions.jpg)
   
6. Log på [Microsoft Security Intelligence som](https://www.microsoft.com/wdsi/filesubmission) virksomhedsbruger med en ikke-administratorkonto for at se, om du har adgang.

 Hvis advarslen ikke løses, efter du har fulgt disse fejlfindingstrin, skal du ringe til Microsoft Support.