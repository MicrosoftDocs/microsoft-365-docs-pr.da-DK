---
title: Trin 5 – Giv en anden medarbejder adgang til OneDrive og Outlook data
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Følg trinnene i denne artikel for at give en anden medarbejder adgang til den tidligere medarbejders OneDrive og Outlook data.
ms.openlocfilehash: 9c56e58de7a7bdbf1cec32ab3fc400c8b3b1b30c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63599394"
---
# <a name="step-5---give-another-employee-access-to-onedrive-and-outlook-data"></a>Trin 5 – Giv en anden medarbejder adgang til OneDrive og Outlook data

Når en medarbejder forlader organisationen, skal du have adgang til deres OneDrive og Outlook, sikkerhedskopier dem og vælge, om du vil give dem til en anden medarbejder.
  
## <a name="access-a-former-users-onedrive-documents"></a>Få adgang til en tidligere brugers OneDrive dokumenter

Hvis du fjerner en brugers licens, men ikke sletter kontoen, kan du give dig selv adgang til indholdet i brugerens OneDrive. Hvis du sletter brugerens konto, har du som standard 30 dage til at få adgang til den tidligere brugers OneDrive data. [Lær, hvordan du indstiller OneDrive opbevaring for slettede brugere](/onedrive/set-retention). Hvis du ikke [gendanner en brugerkonto i](/office365/admin/add-users/restore-user) dette tidsrum, slettes brugerens OneDrive indhold.

Hvis du vil bevare en tidligere brugers OneDrive, skal du først give dig selv adgang til deres OneDrive og derefter flytte de filer, du vil beholde.

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.  

2. Vælg en bruger.

3. På siden med brugeregenskaber skal du **vælge OneDrive**. Under **Få adgang til filer skal** du vælge **Opret link til filer**.

4. Vælg linket for at åbne filplaceringen. Download filerne til din computer, eller vælg Flyt  til eller Kopiér for at flytte eller kopiere dem til din egen OneDrive eller til et delt bibliotek.

> [!NOTE]
> Du kan flytte eller kopiere op til 500 MB filer og mapper ad gangen.<br/>
> Når du flytter eller kopierer dokumenter, der har versionshistorik, flyttes kun den nyeste version.  

Du kan også give en anden bruger adgang til en tidligere medarbejders OneDrive.

1. Log på Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">som</a> global administrator eller SharePoint administrator.

    Hvis du får en meddelelse om, at du ikke har tilladelse til at få adgang til Administration, så har du ikke administratortilladelser i din organisation.

2. I venstre rude skal du **vælge SharePoint** \> **.** Du skal muligvis vælge Vis **alle for** at få vist listen over administrationscentre.

3. Hvis den klassiske SharePoint Administration vises, skal du vælge Åbn den nu øverst på siden **for at åbne** SharePoint Administration.

4. I venstre rude skal du vælge **Flere funktioner**.

5. Under **Brugerprofiler skal** du vælge **Åbn**.

6. Under **Personer skal** du vælge **Administrer brugerprofiler**.

7. Angiv den tidligere medarbejders navn, og vælg **Find**.

8. Højreklik på brugeren, og vælg derefter Administrer ejere **af grupper af websteder**.

9. Føj brugeren til Administratorer **af grupper af websteder,** og vælg **OK**.

10. Brugeren kan nu få adgang til den tidligere medarbejders OneDrive via OneDrive URL-adressen. 

### <a name="revoke-admin-access-to-a-users-onedrive"></a>Tilbagekald administratoradgang til en brugers OneDrive

Du kan give dig selv adgang til indholdet i en brugers OneDrive, men det kan være en god ide at fjerne din adgang, når du ikke længere har brug for den.

1. Log på Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">som</a> global administrator eller SharePoint administrator.

    Hvis du får en meddelelse om, at du ikke har tilladelse til at få adgang til Administration, så har du ikke administratortilladelser i din organisation.

2. I venstre rude skal du **vælge SharePoint** \> **.** Du skal muligvis vælge Vis **alle for** at få vist listen over administrationscentre.

3. Hvis den klassiske SharePoint Administration vises, skal du vælge Åbn den nu øverst på siden **for at åbne** SharePoint Administration.

4. I venstre rude skal du vælge **Flere funktioner**.

5. Under **Brugerprofiler skal** du vælge **Åbn**.

6. Under **Personer skal** du vælge **Administrer brugerprofiler**.

7. Angiv brugerens navn, og vælg **Find**.

8. Højreklik på brugeren, og vælg derefter Administrer ejere **af grupper af websteder**.

9. Fjern den person, der ikke længere skal have adgang til brugerens data, og vælg derefter **OK**.

## <a name="access-the-outlook-data-of-a-former-user"></a>Få adgang Outlook data for en tidligere bruger

Hvis du vil gemme mails, kalender, opgaver og kontakter for den tidligere medarbejder, skal du eksportere oplysningerne til en Outlook-datafil (.pst).
  
1. [Føj den tidligere medarbejders mail](https://support.microsoft.com/office/6e27792a-9267-4aa4-8bb6-c84ef146101b) til din Outlook. Hvis du [nulstiller brugerens adgangskode, kan du](reset-passwords.md) indstille den til noget, som kun du kender.

2. I Outlook skal du vælge **Filer**.

    ![Sådan ser båndet ud i Outlook 2016.](../../media/d7f66ed3-9861-4521-b410-e86a58ab15a7.png)
  
3. Vælg **Åbn &amp; eksportér** \> **Import/Export**.

    ![Import/Export kommando i Backstage-visningen.](../../media/6013919e-d8ce-4902-b7b4-78ff4260a2f8.jpg)
  
4. Vælg **Eksportér til en fil**, og vælg derefter **Næste**.

    ![Indstillingen Eksportér til en fil i guiden Import og eksport.](../../media/458466a0-366b-4fbf-a2db-1919412c6527.jpg)
  
5. Vælg **Outlook datafil (.pst),** og vælg derefter **Næste**.

6. Vælg den konto, du vil eksportere, ved at vælge navnet eller mailadressen, f.eks. Postkasse – Anne Weiler eller anne@contoso.com. Hvis du vil eksportere alt på din konto, herunder mail, kalender, kontakter, opgaver og noter, skal du sørge for,  at afkrydsningsfeltet Medtag undermapper er markeret.

    > [!NOTE]
    > Du kan eksportere én konto ad gangen. Hvis du vil eksportere flere konti, skal du gentage disse trin, når én konto er eksporteret.
  
    ![Dialogboksen Outlook med den øverste mappe markeret og afkrydsningsfeltet Medtag undermapper markeret.](../../media/ce36616f-d76d-4ce2-b517-8ac4874e0971.jpg)
  
7. Vælg **Næste**.

8. Vælg **Gennemse** for at vælge, hvor du vil Outlook filen (.pst). Skriv et  *filnavn*, og vælg derefter **OK for** at fortsætte.

    > [!NOTE]
    > Hvis du har eksporteret tidligere, vises den forrige mappeplacering og det forrige filnavn. Skriv et *andet filnavn,* før du vælger **OK**.
  
9. Hvis du eksporterer til en eksisterende Outlook datafil (.pst), skal **du angive,** hvad der skal gøre, hvis et elementer, der eksporteres, allerede findes i filen. Dette gør du under Indstillinger.

10. Vælg **Udfør**.

Outlook eksporten med det samme, medmindre der Outlook oprettes en ny datafil (.pst), eller der anvendes en adgangskodebeskyttet fil.
  
- Hvis du opretter en Outlook datafil (.pst), kan du vælge at beskytte filen med en adgangskode. Når dialogboksen **Opret Outlook datafil** vises, skal du skrive adgangskoden i felterne Adgangskode  og Bekræft  **adgangskode og** derefter vælge **OK**. Skriv **adgangskoden Outlook dialogboksen Adgangskode** til datafil *, og* vælg derefter **OK**.

- Hvis du eksporterer til en eksisterende Outlook-datafil (.pst), som er adgangskodebeskyttet, skal du skrive adgangskoden i **dialogboksen adgangskode til Outlook-datafil** og derefter vælge **OK**.

Se Eksportere [eller sikkerhedskopiere mail,](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) kontakter og kalender til en Outlook .pst-fil i Outlook 2010.

  > [!NOTE]
  > Din mail er som standard tilgængelig offline i en periode på 12 måneder. Hvis det er nødvendigt, kan du se, hvordan [du øger antallet af tilgængelige data offline](/outlook/troubleshoot/mailboxes/only-subset-items-synchronized).

### <a name="give-another-user-access-to-a-former-users-email"></a>Give en anden bruger adgang til en tidligere brugers mail

Hvis du vil give adgang til mails, kalender, opgaver og kontakter for den tidligere medarbejder til en anden medarbejder, skal du importere oplysningerne til en anden medarbejders Outlook indbakke.

> [!NOTE]
> Du kan også [konvertere den tidligere brugers postkasse til en delt postkasse](/office365/admin/email/convert-user-mailbox-to-shared-mailbox) eller [videresende en tidligere medarbejders mail til en anden medarbejder](/office365/admin/add-users/remove-former-employee#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox).

1. I Outlook skal du gå til **Eksportér** \> **fil &amp;** \> **Import/Export**.

    Dette starter guiden Import og eksport.

2. Vælg **Importér fra et andet program eller en** anden fil, og vælg derefter **Næste**.

    ![Guiden Import og eksport.](../../media/15cdd674-cd7b-492c-8e93-992cfa890f26.jpg)
  
3. Vælg **Outlook datafil (.pst),** og vælg **Næste**.

4. Gå til den .pst-fil, du vil importere.

5. Vælg **,** hvordan du vil håndtere dubletter, under Indstillinger.

6. Vælg **Næste**.

7. Hvis adgangskoden blev tildelt til filen Outlook (.pst), skal du angive adgangskoden og derefter vælge **OK**.

8. Angiv indstillingerne for import af elementer. Som regel behøver standardindstillingerne ikke at blive ændret.

9. Vælg **Udfør**.

> [!NOTE]
> Trinnene forbliver de samme for at få adgang til en eksisterende brugers OneDrive og maildata.

> [!TIP]
> Hvis du kun vil importere eller gendanne nogle få elementer fra en Outlook-datafil (.pst), kan du åbne Outlook datafil. I navigationsruden skal du derefter trække elementerne fra Outlook datafilmapperne til dine eksisterende Outlook mapper.

## <a name="related-content"></a>Relateret indhold

[Tilføj og fjern administratorer på en OneDrive-konto](/sharepoint/manage-user-profiles#add-and-remove-admins-for-a-users-onedrive) (artikel)

[Gendan en slettet OneDrive](/onedrive/restore-deleted-onedrive) (artikel)

[OneDrive opbevaring og sletning](/onedrive/retention-and-deletion) (artikel)

[Del OneDrive filer og mapper](https://support.microsoft.com/office/share-onedrive-files-and-folders-9fcc2f7d-de0c-4cec-93b0-a82024800c07)
