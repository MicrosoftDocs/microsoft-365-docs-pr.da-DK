---
title: Tilpas en politik for arkivering og sletning (MRM) for postkasser
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
- MET150
ms.assetid: ec3587e4-7b4a-40fb-8fb8-8aa05aeae2ce
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Sådan opretter du en brugerdefineret MRM-politik (Messaging Records Management) til arkivering og sletning for automatisk at flytte elementer til en brugers arkivpostkasse.
ms.openlocfilehash: 892f10b7cb57fcc85a7eb364d35730adb2d9c99d
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393496"
---
# <a name="customize-an-archive-and-deletion-policy-for-mailboxes-in-your-organization"></a>Tilpas en politik for arkiv og sletning for postkasser i din organisation

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview administratorer kan oprette en politik for arkivering og sletning, der automatisk flytter elementer til en brugers [arkivpostkasse](archive-mailboxes.md) og automatisk sletter elementer fra postkassen.

Det gør du ved at oprette en MRM-opbevaringspolitik (Messaging Records Management), som du derefter tildeler til postkasser. Denne politik flytter elementer til en brugers arkivpostkasse efter et angivet tidsrum og sletter også elementer fra postkassen, når de har nået en bestemt aldersgrænse.

De faktiske regler, der bestemmer, hvilke elementer der flyttes eller slettes, og hvornår det sker, kaldes opbevaringskoder. Opbevaringskoder er knyttet til en MRM-opbevaringspolitik, der igen tildeles en brugers postkasse. En opbevaringskode anvender opbevaringsindstillinger for individuelle meddelelser og mapper i en brugers postkasse. Den definerer, hvor længe en meddelelse forbliver i postkassen, og hvilken handling der udføres, når meddelelsen når den angivne opbevaringsalder. Når en meddelelse når sin opbevaringsalder, flyttes den enten til brugerens arkivpostkasse, eller den slettes.
  
Trinnene i denne artikel konfigurerer en politik for arkivering og opbevaring for en fiktiv organisation ved navn Alpine House. Konfiguration af denne politik omfatter følgende opgaver:
  
- Aktivér en arkivpostkasse for alle brugere i organisationen. Denne procedure giver brugerne mere postkasselager og er påkrævet, så en opbevaringspolitik automatisk kan flytte elementer til arkivpostkassen. En bruger kan også manuelt flytte elementer til sin arkivpostkasse til arkiveringslager.

- Opret tre brugerdefinerede opbevaringskoder for at udføre følgende handlinger:

  - Flyt automatisk elementer, der er 3 år gamle, til brugerens arkivpostkasse. Hvis du flytter elementer til arkivpostkassen, frigøres der plads i en brugers primære postkasse.

  - Slet automatisk elementer, der er 5 år gamle, fra mappen Slettet post. Dette frigør også plads i brugerens primære postkasse. Brugerens får mulighed for at gendanne disse elementer, hvis det er nødvendigt. Se fodnoten i afsnittet [Flere oplysninger](#more-information) for at få flere oplysninger. 

  - Slet automatisk (og permanent) elementer, der er 7 år gamle, fra både den primære postkasse og arkivpostkassen. På grund af overholdelsesreglerne er nogle organisationer forpligtet til at bevare mailen i et bestemt tidsrum. Når denne tidsperiode udløber, kan det være en god idé for en organisation at fjerne disse elementer permanent fra brugerpostkasser.

- Opret en ny opbevaringspolitik, og føj de nye brugerdefinerede opbevaringskoder til den. Derudover skal du også føje indbyggede opbevaringskoder til den nye opbevaringspolitik. Dette omfatter personlige mærker, som brugerne kan tildele til elementer i deres postkasse. Du skal også tilføje en opbevaringskode, der flytter elementer fra mappen Gendanbare elementer i brugerens primære postkasse til mappen Gendanbare elementer i deres arkivpostkasse. Denne handling hjælper med at frigøre plads i en brugers mappe Med genoprettelige elementer, når brugerens postkasse er sat i venteposition.

Du kan følge nogle af eller alle trinnene i denne artikel for at konfigurere en politik for arkiv og sletning for postkasser i din egen organisation. Vi anbefaler, at du tester denne proces på nogle få postkasser, før du implementerer den på alle postkasser i din organisation.
  
## <a name="before-you-set-up-an-archive-and-deletion-policy"></a>Før du konfigurerer en politik for arkivering og sletning

- Du skal være global administrator i din organisation for at kunne udføre trinnene i denne artikel.

- Når du opretter en ny brugerkonto og tildeler brugeren en Exchange Online licens, oprettes der automatisk en postkasse for brugeren. Når postkassen oprettes, tildeles den automatisk en standardopbevaringspolitik med navnet Standard-MRM-politik. I denne artikel skal du oprette en ny MRM-opbevaringspolitik og derefter tildele den til brugerpostkasser og erstatte standard-MRM-politikken. En postkasse kan kun tildeles én MRM-opbevaringspolitik på én gang.

- Hvis du vil vide mere om opbevaringskoder og MRM-opbevaringspolitikker i Exchange Online, skal du se [Opbevaringskoder og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

## <a name="step-1-enable-archive-mailboxes-for-users"></a>Trin 1: Aktivér arkivpostkasser for brugere

Det første trin er at sikre, at hver bruger i din organisation har en arkivpostkasse. En brugers arkivpostkasse skal være aktiveret, så en opbevaringskode med opbevaringshandlingen "Flyt til arkiv" kan flytte elementet, når opbevaringsalderen udløber.

Du kan finde oplysninger om, hvordan du aktiverer arkivpostkasser, [under Aktivér arkivpostkasser i Microsoft Purview-compliance-portal](enable-archive-mailboxes.md).
  
> [!NOTE]
> Du kan aktivere arkivpostkasser når som helst under denne proces, så længe de er aktiveret på et tidspunkt, før du fuldfører processen. Hvis en arkivpostkasse ikke er aktiveret, udføres der ingen handling på elementer, hvor der er tildelt en politik for arkiv eller sletning.

## <a name="step-2-create-new-retention-tags-for-the-archive-and-deletion-policies"></a>Trin 2: Opret nye opbevaringskoder for arkiverings- og sletningspolitikkerne

I dette trin skal du oprette de tre brugerdefinerede opbevaringskoder, der tidligere er beskrevet.
  
- Alpine House 3 Year Move to Archive (brugerdefineret arkivpolitik)

- Sletning af Alpine House 7 år permanent (brugerdefineret politik for sletning)

- Slettede elementer i Alpine House 5 år til sletning og gendannelse (brugerdefineret kode for mappen Slettet post)

Hvis du vil oprette nye opbevaringstags, skal du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> i din Exchange Online organisation. Sørg for at bruge den klassiske version af EAC.
  
1. Gå til , [https://admin.protection.outlook.com/ecp/](https://admin.protection.outlook.com/ecp/) og log på med dine legitimationsoplysninger.
  
2. I EAC skal du gå til **Administration af** >  **overholdelseRetention-mærker**

    Der vises en liste over opbevaringskoderne for din organisation.

### <a name="create-a-custom-archive-default-policy-tag"></a>Opret et standardpolitikmærke for et brugerdefineret arkiv
  
Først skal du oprette et DPT (Custom Archive Default Policy Tag), der flytter elementer til arkivpostkassen efter 3 år.
  
1. På siden **Opbevaringskoder** skal du vælge **Nyt mærkeNyt**![ ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) Vælg derefter **Anvendt automatisk på hele postkassen (standard).**

2. På siden **Ny kode, der automatisk anvendes på hele postkassen (standard),** skal du udfylde følgende felter: 

    ![Indstillinger til at oprette et nyt standardpolitikmærke for arkivet.](../media/41c0a43c-9c72-44e0-8947-da0831896432.png)
  
   1. **Navn** Skriv et navn til den nye opbevaringskode. 

   2. **Opbevaringshandling** Vælg **Flyt til arkiv** for at flytte elementer til arkivpostkassen, når opbevaringsperioden udløber.

   3. **Opbevaringsperioden** Vælg **Når elementet når følgende alder (i dage),** og angiv derefter varigheden af opbevaringsperioden. I dette scenarie flyttes elementer til arkivpostkassen efter 1095 dage (3 år).

   4. **Kommentar** (valgfrit) Skriv en kommentar, der forklarer formålet med den brugerdefinerede opbevaringskode.

3. Vælg **Gem** for at oprette det brugerdefinerede arkiv DPT.

    Den nye arkiv-DPT vises på listen over opbevaringskoder.

### <a name="create-a-custom-deletion-default-policy-tag"></a>Opret en brugerdefineret standardpolitikkode for sletning
  
Derefter skal du oprette en anden brugerdefineret DPT, men denne er en politik for sletning, der sletter elementer permanent efter 7 år.
  
1. På siden **Opbevaringskoder** skal du vælge **Nyt mærkeNyt**![ ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) Vælg derefter **Anvendt automatisk på hele postkassen (standard).**

2. På siden **Ny kode, der automatisk anvendes på hele postkassen (standard),** skal du udfylde følgende felter: 

    ![Indstillinger til at oprette et nyt standardpolitikmærke for sletning.](../media/f1f0ff62-eec9-4824-8e7c-d93dcfb09a79.png)
  
   1. **Navn** Skriv et navn til den nye opbevaringskode. 

   2. **Opbevaringshandling** Vælg **Slet permanent** for at fjerne elementer fra postkassen, når opbevaringsperioden udløber.

   3. **Opbevaringsperioden** Vælg **Når elementet når følgende alder (i dage),** og angiv derefter varigheden af opbevaringsperioden. I dette scenarie fjernes elementer efter 2555 dage (7 år).

   4. **Kommentar** (valgfrit) Skriv en kommentar, der forklarer formålet med den brugerdefinerede opbevaringskode. 

3. Vælg **Gem** for at oprette DPT for brugerdefineret sletning. 

    Den nye DPT til sletning vises på listen over opbevaringskoder.

### <a name="create-a-custom-retention-policy-tag-for-the-deleted-items-folder"></a>Opret en brugerdefineret opbevaringspolitikkode for mappen Slettet post
  
Den sidste opbevaringskode, der blev oprettet, er et brugerdefineret opbevaringspolitikmærke (RPT) for mappen Slettet post. Dette mærke sletter elementer i mappen Slettet post efter 5 år og giver en genoprettelsesperiode, hvor brugerne kan bruge værktøjet Gendan slettet post til at gendanne et element.
  
1. På siden **Opbevaringskoder** skal du vælge **Nyt mærke** ![Nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) Vælg derefter **Anvendt automatisk på en standardmappe**.

2. På siden **Ny kode, der anvendes automatisk på en standardmappe** skal du udfylde følgende felter:

    ![Indstillinger til at oprette en ny opbevaringspolitikkode for mappen Slettet post.](../media/6f3104bd-5edb-48ac-884d-5fe13d81dd1d.png)
  
   1. **Navn** Skriv et navn til den nye opbevaringskode. 

   2. **Anvend dette mærke på følgende standardmappe** Vælg **Slettet post** på rullelisten.

   3. **Opbevaringshandling** Vælg **Slet og Tillad gendannelse** for at slette elementer, når opbevaringsperioden udløber, men giv brugerne tilladelse til at gendanne et slettet element inden for opbevaringsperioden for slettet element (som standard er 14 dage).

   4. **Opbevaringsperioden** Vælg **Når elementet når følgende alder (i dage),** og angiv derefter varigheden af opbevaringsperioden. I dette scenarie slettes elementer efter 1825 dage (5 år).

   5. **Kommentar** (valgfrit) Skriv en kommentar, der forklarer formålet med den brugerdefinerede opbevaringskode. 

3. Vælg **Gem** for at oprette den brugerdefinerede RPT til mappen Slettet post.

    Den nye RPT vises på listen over opbevaringskoder.

## <a name="step-3-create-a-new-retention-policy"></a>Trin 3: Opret en ny opbevaringspolitik

Når du har oprettet de brugerdefinerede opbevaringskoder, er det næste trin at oprette en ny opbevaringspolitik og tilføje opbevaringskoderne. Du skal tilføje de tre brugerdefinerede opbevaringskoder, du oprettede i trin 2, og de indbyggede mærker, der blev nævnt i det første afsnit. I trin 4 skal du tildele denne nye opbevaringspolitik til brugerpostkasser.
  
1. I EAC skal du gå til **Administration af** >  **overholdelseRetention-politikker**.

2. På siden **Opbevaringspolitikker** skal du vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

3. Skriv et navn til den nye opbevaringspolitik i feltet **Navn** . for eksempel **Alpine House Archive og Deletion Policy**.

4. Under **Opbevaringskoder** skal du vælge **Tilføj** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

    Der vises en liste over opbevaringskoderne i din organisation. Bemærk, at de brugerdefinerede mærker, du oprettede i trin 2, vises.

5. Tilføj de 9 opbevaringskoder, der er fremhævet på følgende skærmbillede (disse mærker er beskrevet mere detaljeret i afsnittet [Flere oplysninger](#more-information) ). Hvis du vil tilføje et opbevaringsmærke, skal du vælge det og derefter vælge **Tilføj**.

    ![Føj opbevaringskoder til den nye opbevaringspolitik.](../media/d8e87176-0716-4238-9e6a-7c4af35541dc.png)
  
    > [!TIP]
    > Du kan vælge flere opbevaringskoder ved at holde **Ctrl** nede og derefter klikke på hvert mærke. 
  
6. Når du har tilføjet opbevaringskoderne, skal du vælge **OK**.

7. På siden **Ny opbevaringspolitik** skal du vælge **Gem** for at oprette den nye politik.

    Den nye opbevaringspolitik vises på listen. Vælg den for at få vist de opbevaringskoder, der er knyttet til den, i detaljeruden.

    ![Den nye opbevaringspolitik og listen over sammenkædede opbevaringsmærker.](../media/63bc45e6-110b-4dc9-a85f-8eb1961a8258.png)
  
## <a name="step-4-assign-the-new-retention-policy-to-user-mailboxes"></a>Trin 4: Tildel den nye opbevaringspolitik til brugerpostkasser

Når der oprettes en ny postkasse, tildeles den som standard en opbevaringspolitik med navnet Standard-MRM-politik. I dette trin skal du erstatte denne opbevaringspolitik ved at tildele den nye opbevaringspolitik, du oprettede i trin 3, til brugerpostkasserne i din organisation. Erstatning er påkrævet, fordi der kun kan tildeles én MRM-opbevaringspolitik til en postkasse ad gangen. I dette trin forudsættes det, at du tildeler den nye politik til alle postkasser i organisationen.
  
1. I EAC skal du gå til **ModtagereMailboxes** > .

    Der vises en liste over alle brugerpostkasser i din organisation.

2. Vælg alle postkasserne ved at klikke på den første på listen, holde **Skift** nede og derefter klikke på den sidste på listen. 

3. Vælg **Flere indstillinger** under **Masseredigering** i detaljeruden i EAC.

4. Under **Opbevaringspolitik** skal du vælge **Opdater**.

5. Vælg den opbevaringspolitik, du oprettede i trin 3, på rullelisten **Vælg opbevaringspolitikken** på siden **Massetildel opbevaringspolitik**. for eksempel **Alpine House Archive og opbevaringspolitik**.

6. Vælg **Gem** for at gemme den nye tildeling af opbevaringspolitik.

7. Sådan bekræfter du, at den nye opbevaringspolitik er tildelt til postkasser:

   1. Vælg en postkasse på siden **Postkasser**, og vælg derefter **Rediger** ![Rediger.](../media/d7dc7e5f-17a1-4eb9-b42d-487db59e2e21.png)

   2. Vælg **Postkassefunktioner** på siden med egenskaber for postkassen for den valgte bruger.

   Navnet på den nye politik, der er tildelt postkassen, vises på rullelisten **Opbevaringspolitik** .

## <a name="optional-step-5-run-the-managed-folder-assistant-to-apply-the-new-settings"></a>(Valgfrit) Trin 5: Kør Assistent til administreret mappe for at anvende de nye indstillinger

Når du har anvendt den nye opbevaringspolitik på postkasser i trin 4, kan det tage op til syv dage i Exchange Online, før de nye opbevaringsindstillinger anvendes på postkasserne. Det skyldes, at en proces, der kaldes *Den Administrerede mappeassistent* , behandler postkasser mindst én gang hver 7. dag. I stedet for at vente på, at Managed Folder Assistant kører, kan du gennemtvinge, at dette sker, ved at køre cmdlet'en **Start-ManagedFolderAssistant** i Exchange Online PowerShell.

 **Hvad sker der, når du kører Assistent til administrerede mapper?** Den anvender indstillingerne i opbevaringspolitikken ved at undersøge elementer i postkassen og afgøre, om de er underlagt opbevaring. Derefter stemples elementer, der skal opbevares, med den relevante opbevaringskode, og derefter udføres den angivne opbevaringshandling for elementer, der har overskredet deres opbevaringsalder.
  
Her er trinnene til at oprette forbindelse til Exchange Online PowerShell og derefter køre Assistent til administrerede mapper på hver postkasse i din organisation.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Kør følgende to kommandoer for at starte Assistent til administreret mappe for alle brugerpostkasser i din organisation.

    ```powershell
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    ```

    ```powershell
    $Mailboxes.Identity | Start-ManagedFolderAssistant
    ```

Det var det hele! Du har konfigureret en politik for arkivering og sletning for Alpine House-organisationen.

### <a name="more-information-about-the-managed-folder-assistant"></a>Flere oplysninger om Assistent til administrerede mapper

Som tidligere nævnt behandler Den Administrerede mappeassistent postkasser mindst én gang hver 7. dag. Det er derfor muligt, at en postkasse kan behandles oftere af Assistent til administrerede mapper. Administratorer kan heller ikke forudsige, næste gang en postkasse behandles af Assistent til administrerede mapper, hvilket er en af grundene til, at det kan være en god idé at køre den manuelt. 

Men hvis du midlertidigt vil forhindre assistenten for administrerede mapper i at anvende de nye opbevaringsindstillinger på en postkasse, kan du køre `Set-Mailbox -ElcProcessingDisabled $true` kommandoen for midlertidigt at deaktivere Assistent til administrerede mapper i at behandle en postkasse. 

Kør kommandoen for at aktivere Assistent til administrerede mapper igen for en postkasse `Set-Mailbox -ElcProcessingDisabled $false` . 

Hvis en postkassebruger har en deaktiveret konto, flyttes elementer ikke til arkivpostkassen for den pågældende postkasse.
  
## <a name="optional-step-6-make-the-new-retention-policy-the-default-for-your-organization"></a>(Valgfrit) Trin 6: Gør den nye opbevaringspolitik til standard for din organisation

I trin 4 skal du tildele den nye opbevaringspolitik til eksisterende postkasser. Men du kan konfigurere Exchange Online, så den nye opbevaringspolitik tildeles til nye postkasser, der oprettes i fremtiden. 

Det gør du ved at bruge Exchange Online PowerShell til at opdatere organisationens standardpostkasseplan. En *postkasseplan* er en skabelon, der automatisk konfigurerer egenskaber for nye postkasser.  I dette valgfrie trin kan du erstatte den aktuelle opbevaringspolitik, der er tildelt til postkasseplanen (som standard standard MRM-politikken) med den MRM-opbevaringspolitik, du oprettede i trin 3. Når du har opdateret postkasseplanen, tildeles den nye MRM-opbevaringspolitik til nye postkasser.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende kommando for at få vist oplysninger om postkasseplaner i din organisation.

    ```powershell
    Get-MailboxPlan | Format-Table DisplayName,RetentionPolicy,IsDefault
    ```
    
    Bemærk den postkasseplan, der er angivet som standard.

3. Kør følgende kommando for at tildele den nye MRM-opbevaringspolitik, som du oprettede i trin 3 (f.eks **. Alpine House Archive og Retention Policy**), til standardpostkasseplanen. I dette eksempel antages det, at navnet på standardpostkasseplanen er **ExchangeOnlineEnterprise**.
    
    ```powershell
    Set-MailboxPlan "ExchangeOnlineEnterprise" -RetentionPolicy "Alpine House Archive and Retention Policy"
    ```

4. Du kan køre kommandoen igen i trin 2 for at bekræfte, at den MRM-opbevaringspolitik, der er tildelt standardpostkasseplanen, er blevet ændret.

## <a name="more-information"></a>Flere oplysninger

- Opbevaringsalder for postkasseelementer beregnes fra leveringsdatoen. Eller fra oprettelsesdatoen for elementer, f.eks. kladdemeddelelser, der ikke sendes, men som er oprettet af brugeren. Når Assistent til administreret mappe behandler elementer i en postkasse, stemples en startdato og en udløbsdato for alle elementer, der har opbevaringskoder, med handlingen Slet og Tillad gendannelse eller Slet permanent. Elementer med en arkivkode stemples med en flyttedato.

- Følgende tabel indeholder flere oplysninger om hver opbevaringskode for den brugerdefinerede MRM-opbevaringspolitik i denne artikel.

    | Opbevaringskode | Hvad dette mærke gør | Indbygget eller brugerdefineret? | Type |
    |:-----|:-----|:-----|:-----|
    |Alpine House 3 År Flyt til Arkiv  <br/> |Flytter elementer, der er 1095 dage (3 år), til arkivpostkassen.  <br/> |Brugerdefineret (se [Trin 2: Opret nye opbevaringskoder til politikker for arkivering og sletning](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Standardpolitikmærke (arkiv); dette mærke anvendes automatisk på hele postkassen.  <br/> |
    |Sletning af Alpine House 7 år permanent  <br/> |Sletter permanent elementer i den primære postkasse eller arkivpostkassen, når de er 7 år gamle.  <br/> |Brugerdefineret (se [Trin 2: Opret nye opbevaringskoder til politikker for arkivering og sletning](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Standardpolitikmærke (sletning); dette mærke anvendes automatisk på hele postkassen.  <br/> |
    |Slettede elementer i Alpine House 5 år – Slet og Tillad gendannelse  <br/> |Sletter elementer fra mappen Slettet post, der er 5 år gammel. Brugerne kan gendanne disse elementer i op til 14 dage, efter at de er slettet.<sup>\*</sup> <br/> |Brugerdefineret (se [Trin 2: Opret nye opbevaringskoder til politikker for arkivering og sletning](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Opbevaringspolitikmærke (slettede elementer); dette mærke anvendes automatisk på elementer i mappen Slettet post.  <br/> |
    |Elementer, der kan gendannes, 14 dage, flyt til arkiv  <br/> |Flytter elementer, der har været i mappen Elementer, der kan gendannes, i 14 dage til mappen Elementer, der kan gendannes i arkivpostkassen.  <br/> |Indbygget  <br/> |Opbevaringspolitikmærke (elementer, der kan genoprettes); dette mærke anvendes automatisk på elementer i mappen Elementer, der kan gendannes.  <br/> |
    |Uønsket mail  <br/> |Sletter permanent elementer, der har været i mappen Uønsket mail i 30 dage. Brugerne kan gendanne disse elementer i op til 14 dage, efter at de er slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Opbevaringspolitikmærke (uønsket mail); dette mærke anvendes automatisk på elementer i mappen Uønsket mail.  <br/> |
    |1 måned - sletning  <br/> |Sletter permanent elementer, der er 30 dage gamle. Brugerne kan gendanne disse elementer i op til 14 dage, efter at de er slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |1 års sletning  <br/> |Sletter permanent elementer, der er 365 dage gamle. Brugerne kan gendanne disse elementer i op til 14 dage, efter at de er slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |Slet aldrig  <br/> |Denne kode forhindrer, at elementer slettes af en opbevaringspolitik.  <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |Personligt 1 års flytning til arkiv  <br/> |Flytter elementer til arkivpostkassen efter 1 år.  <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |

    > <sup>\*</sup>Brugerne kan bruge værktøjet Gendan slettede elementer i Outlook og Outlook på internettet (tidligere kaldet Outlook Web App) til at gendanne et slettet element inden for opbevaringsperioden for slettede elementer, hvilket som standard er 14 dage i Exchange Online. En administrator kan bruge Windows PowerShell til at øge opbevaringsperioden for slettede elementer til højst 30 dage. Du kan finde flere oplysninger [under: Gendan slettede elementer i Outlook for Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce), og [rediger opbevaringsperioden for slettede elementer for en postkasse i Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention).
  
- Brug af koden **Flyt til arkivopbevaring i 14 dage, der kan genoprettes** , hjælper med at frigøre lagerplads i mappen Gendanbare elementer i brugerens primære postkasse. Dette er nyttigt, når en brugers postkasse er sat i venteposition, hvilket betyder, at intet slettes permanent fra brugerens postkasse. Uden at flytte elementer til arkivpostkassen er det muligt, at lagerkvoten for mappen Gendanbare elementer i den primære postkasse nås. Du kan finde flere oplysninger om dette, og hvordan du undgår det, under [Forøg kvoten for genoprettelige elementer for postkasser i venteposition](./increase-the-recoverable-quota-for-mailboxes-on-hold.md).
