---
title: Foretag fejlfinding af fejl i MSI-portalen, der skyldes administratorblokering
description: Foretag fejlfinding af fejl i MSI-portalen
ms.reviewer: ''
keywords: sikkerhed, eksempel indsendelse hjælp, malware fil, virus fil, trojanske fil, sende, sende, sende til Microsoft, indsende en prøve, virus, trojan, orm, uopdaget, ikke registrere, email microsoft, email malware, jeg tror, det er malware, jeg tror det er en virus, hvor kan jeg sende en virus, er dette en virus, MSE, ikke registrere, ingen signatur, ingen opdagelse, mistænkelig fil,  MMPC, Microsoft Malware Protection Center, forskere, analytiker, WDSI, security intelligence
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
ms.openlocfilehash: 544e96bd0a3985856f47bc8df424a2c2932f3c7e
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665662"
---
# <a name="troubleshooting-malware-submission-errors-caused-by-administrator-block"></a>Fejlfinding i forbindelse med indsendelse af malwarefejl forårsaget af administratorblokering

I nogle tilfælde kan en administratorblokering medføre afsendelsesproblemer, når du forsøger at sende en potentielt inficeret fil til analyse [på Microsoft Security Intelligence-webstedet](https://www.microsoft.com/wdsi) . I følgende proces kan du se, hvordan du løser dette problem.

## <a name="review-your-settings"></a>Gennemse dine indstillinger

Åbn [indstillingerne for dit Azure Enterprise-program](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/). Under **VirksomhedsprogrammerBrugere** >   **kan give samtykke til, at apps får adgang til virksomhedsdata på deres vegne**, skal du kontrollere, om Ja eller Nej er valgt.

- Hvis **Nej** er valgt, skal en Azure AD-administrator for kundelejer give samtykke til organisationen. Afhængigt af konfigurationen med Azure AD kan brugerne muligvis sende en anmodning direkte fra den samme dialogboks. Hvis der ikke er nogen mulighed for at bede om administratorsamtykke, skal brugerne anmode om, at disse tilladelser føjes til deres Azure AD-administrator. Gå til følgende afsnit for at få flere oplysninger.

- Hvis **Ja** er valgt, skal du sikre, at indstillingen Windows Defender Security Intelligence-app **er aktiveret, så brugerne kan logge på?** er angivet til **Ja** [i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d). Hvis **Nej** er valgt, skal du anmode en Azure AD-administrator om at aktivere den.

## <a name="implement-required-enterprise-application-permissions"></a>Implementer påkrævede tilladelser til virksomhedsprogrammer

Denne proces kræver en global administrator eller programadministrator i lejeren.

1. Åbn [indstillinger for virksomhedsprogram](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/4a918a14-4069-4108-9b7d-76486212d75d).
2. Vælg **Tildel administratorsamtykke til organisation**.
3. Hvis du kan gøre det, skal du gennemse de API-tilladelser, der kræves til dette program, som vist på følgende billede. Giv samtykke til lejeren.

    ![give samtykkebillede.](../../media/security-intelligence-images/msi-grant-admin-consent.jpg)

4. Hvis administratoren får vist en fejl under forsøg på at give samtykke manuelt, kan du prøve enten [Mulighed 1](#option-1-approve-enterprise-application-permissions-by-user-request) eller [Mulighed 2](#option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin) som mulige løsninger.

## <a name="option-1-approve-enterprise-application-permissions-by-user-request"></a>Mulighed 1 Godkend tilladelser til virksomhedsprogrammer efter brugeranmodning

> [!NOTE]
> Dette er i øjeblikket en prøveversionsfunktion.

Azure Active Directory administratorer skal give brugerne mulighed for at anmode om administratorsamtykke til apps. Kontrollér, at indstillingen er konfigureret til **Ja** i [virksomhedsprogrammer](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/UserSettings/menuId/).

![Brugerindstillinger for virksomhedsprogrammer.](../../media/security-intelligence-images/msi-enterprise-app-user-setting.jpg)

Du kan få flere oplysninger i [Konfigurer arbejdsproces for administratorsamtykke](/azure/active-directory/manage-apps/configure-admin-consent-workflow).

Når denne indstilling er bekræftet, kan brugerne gå gennem virksomhedens kundelogon hos [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) og sende en anmodning om administratorsamtykke, herunder begrundelse.

![Contoso-logonflow.](../../media/security-intelligence-images/msi-contoso-approval-required.png)

Administratoren kan gennemse og godkende anmodninger om programtilladelser for [Anmodninger om samtykke fra Azure-administratorer](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AccessRequests/menuId/).

Når du har givet samtykke, kan alle brugere i lejeren bruge programmet.

## <a name="option-2-provide-admin-consent-by-authenticating-the-application-as-an-admin"></a>Mulighed 2 Giv administratorsamtykke ved at godkende programmet som administrator

Denne proces kræver, at globale administratorer gennemgår Enterprise-kundelogonflowet hos [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission).

![Flow for logon til samtykke.](../../media/security-intelligence-images/msi-microsoft-permission-required.jpg)

Administratorer gennemser derefter tilladelserne, og sørg for at vælge **Samtykke på vegne af din organisation**, og vælg derefter **Acceptér**.

Alle brugere i lejeren kan nu bruge dette program.

## <a name="option-3-delete-and-readd-app-permissions"></a>Mulighed 3: Slet og læste apptilladelser

Hvis ingen af disse indstillinger løser problemet, kan du prøve følgende trin (som administrator):

1. Fjern tidligere konfigurationer for programmet. Gå til [Virksomhedsprogrammer,](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Properties/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/982e94b2-fea9-4d1f-9fca-318cda92f90b) og vælg **Slet**.

   ![Slet apptilladelser.](../../media/security-intelligence-images/msi-properties.png)

2. Hent Lejer-id fra [Egenskaber](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).

3. Erstat {tenant-id} med den specifikke lejer, der skal give samtykke til dette program i URL-adressen nedenfor. Kopiér denne URL-adresse til en browser. Resten af parametrene er allerede fuldført.
``https://login.microsoftonline.com/{tenant-id}/v2.0/adminconsent?client_id=f0cf43e5-8a9b-451c-b2d5-7285c785684d&state=12345&redirect_uri=https%3a%2f%2fwww.microsoft.com%2fwdsi%2ffilesubmission&scope=openid+profile+email+offline_access``

   ![Tilladelser skal angives.](../../media/security-intelligence-images/msi-microsoft-permission-requested-your-organization.png)

4. Gennemse de tilladelser, der kræves af programmet, og vælg derefter **Acceptér**.

5. Bekræft, at tilladelserne anvendes i [Azure Portal](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ManagedAppMenuBlade/Permissions/appId/f0cf43e5-8a9b-451c-b2d5-7285c785684d/objectId/ce60a464-5fca-4819-8423-bcb46796b051).

   ![Gennemse, at der er anvendt tilladelser.](../../media/security-intelligence-images/msi-permissions.jpg)

6. Log på [Microsoft Security Intelligence](https://www.microsoft.com/wdsi/filesubmission) som virksomhedsbruger med en konto, der ikke er administrator, for at se, om du har adgang.

 Hvis advarslen ikke løses efter at have fulgt disse fejlfindingstrin, skal du ringe til Microsoft Support.