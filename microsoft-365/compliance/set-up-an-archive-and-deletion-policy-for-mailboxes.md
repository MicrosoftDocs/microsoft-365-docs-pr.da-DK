---
title: Tilpasse et arkiv og en sletningspolitik (MRM) for postkasser i organisationen
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
description: Sådan opretter du en brugerdefineret MRM-arkiverings- og sletningspolitik (Messaging Records Management) for automatisk at flytte elementer til en brugers arkivpostkasse.
ms.openlocfilehash: 192bed6be6c3129410f4e51144402c6c19e12d37
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587718"
---
# <a name="customize-an-archive-and-deletion-policy-for-mailboxes-in-your-organization"></a>Tilpasse en arkiverings- og sletningspolitik for postkasser i organisationen

Microsoft 365 til overholdelse af regler og standarder kan oprette en arkiverings- og sletningspolitik, der automatisk flytter elementer til en [](archive-mailboxes.md) brugers arkivpostkasse og automatisk sletter elementer fra postkassen.

Det gør du ved at oprette en MRM-opbevaringspolitik (Messaging Records Management), som er tildelt postkasser, og ved at flytte elementer til en brugers arkivpostkasse efter en bestemt tidsperiode, og som også sletter elementer fra postkassen, når de når en bestemt aldersgrænse. 

De faktiske regler, der bestemmer, hvilke elementer der flyttes eller slettes, og hvornår det sker, kaldes opbevaringsmærker. Opbevaringsmærker er knyttet til en MRM opbevaringspolitik, der igen er tildelt til en brugers postkasse. Et opbevaringsmærke anvender opbevaringsindstillinger på individuelle meddelelser og mapper i en brugers postkasse. Den definerer, hvor lang tid en meddelelse forbliver i postkassen, og hvilken handling der skal tages, når meddelelsen når den angivne opbevaringsalder. Når en meddelelse når opbevaringsalderen, flyttes den enten til brugerens arkivpostkasse, eller den slettes.
  
Trinnene i denne artikel konfigureret en arkiverings- og opbevaringspolitik for den fiktive organisation Alpine House. Konfiguration af denne politik omfatter følgende opgaver:
  
- Aktivering af en arkivpostkasse for alle brugere i organisationen. Dette giver brugerne yderligere lagerplads til postkassen og er påkrævet, så en opbevaringspolitik kan flytte elementer til arkivpostkassen. Den gør det også muligt for en bruger at gemme arkiveringsoplysninger ved at flytte elementer til deres arkivpostkasse.

- Oprettelse af tre brugerdefinerede opbevaringsmærker, som gør følgende:

  - Flytter automatisk elementer, der er 3 år gamle til brugerens arkivpostkasse. Ved at flytte elementer til arkivpostkassen, frigøres der plads i en brugers primære postkasse.

  - Sletter automatisk elementer, der er 5 år gamle fra mappen Slettet post. Dette frier også plads i brugerens primære postkasse. Brugeren har mulighed for at gendanne disse elementer, hvis det er nødvendigt. Se fodnoten Flere oplysninger [for at](#more-information) få mere at vide. 

  - Sletter automatisk (og permanent) elementer, der er 7 år gamle fra både primær- og arkivpostkasse. På grund af overholdelse af regler skal nogle organisationer bevare mail i en bestemt tidsperiode. Når dette tidsrum udløber, kan det være en ide for en organisation at fjerne disse elementer permanent fra brugerpostkasserne.

- Opret en ny opbevaringspolitik, og tilføj de nye brugerdefinerede opbevaringsmærker til den. Desuden kan du også tilføje indbyggede opbevaringsmærker til den nye opbevaringspolitik. Dette omfatter personlige mærker, som brugere kan tildele til elementer i deres postkasse. Du kan også tilføje et opbevaringsmærke, der flytter elementer fra mappen Genoprettelige elementer i brugerens primære postkasse til mappen genoprettelige elementer i arkivpostkassen. Dette hjælper med at frigøre plads i en brugers mappe Genoprettelige elementer, når brugerens postkasse er placeret i venteposition.

Du kan følge nogle eller alle trinnene i denne artikel for at konfigurere en arkiverings- og sletningspolitik for postkasser i din egen organisation. Vi anbefaler, at du tester denne proces på et par postkasser, før du implementerer den på alle postkasser i organisationen.
  
## <a name="before-you-set-up-an-archive-and-deletion-policy"></a>Før du konfigurerer en arkiverings- og sletningspolitik

- Du skal være global administrator i organisationen for at udføre trinnene i dette emne. 

- Når du opretter en ny brugerkonto og tildeler brugeren Exchange Online licens, oprettes der automatisk en postkasse til brugeren. Når postkassen oprettes, tildeles den automatisk en standardopbevaringspolitik, der hedder MRM Standardpolitik. I denne artikel skal du oprette en ny opbevaringspolitik og derefter tildele den til brugerpostkasser og erstatte MRM-standardpolitikken. En postkasse kan kun have én opbevaringspolitik tildelt til den ad gangen.

- Du kan få mere at vide om opbevaringsmærker og opbevaringspolitikker Exchange Online opbevaringsmærker i [Opbevaringsmærker og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies).

## <a name="step-1-enable-archive-mailboxes-for-users"></a>Trin 1: Aktivér arkivpostkasser for brugere

Det første trin er at aktivere arkivpostkassen for hver bruger i organisationen. En brugers arkivpostkasse skal være aktiveret, så et opbevaringsmærke med en "Flyt til Arkiv"-opbevaringshandling kan flytte elementet efter opbevaringsalderen udløber.
  
> [!NOTE]
> Du kan aktivere arkivpostkasser når som helst under denne proces, så længe de er aktiveret, før du har fuldført processen. Hvis en arkivpostkasse ikke er aktiveret, sker der ikke noget med de elementer, der er tildelt arkiverings- eller sletningspolitik.
  
1. Gå til <https://compliance.microsoft.com>.

2. Log på med din globale administratorkonto.
    
3. Klik på Microsoft 365 Overholdelsescenter under **fanen Arkivér**, og klik **derefter på** fanen Arkivér.

    Der vises en liste over postkasser i organisationen, og om den tilsvarende arkivpostkasse er aktiveret eller deaktiveret.

4. Markér alle postkasserne ved at klikke på den første på listen, holde **Skift** nede og derefter klikke på den sidste på listen.

    > [!TIP]
    > Dette trin forudsætter, at ingen arkivpostkasser er aktiveret. Hvis du har postkasser med arkiv aktiveret, skal du holde **Ctrl** nede og klikke på hver postkasse, der har en deaktiveret arkivpostkasse. Eller du kan klikke på  kolonneoverskriften Arkivpostkasse for at sortere rækkerne baseret på, om arkivpostkassen er aktiveret eller deaktiveret for at gøre det nemmere at vælge postkasser.
  
5. Klik på Aktivér under **Masseredigering i detaljeruden**.

    Der vises en advarsel, der fortæller, at elementer, der er ældre end to år, flyttes til den nye arkivpostkasse. Dette skyldes, at standardopbevaringspolitikken, der er tildelt en ny brugerpostkasse, når den oprettes, har et arkiveringsstandardpolitikmærke, der har en opbevaringsalder på 2 år. Det brugerdefinerede arkiveringsstandardpolitikmærke, som du opretter i trin 2, har en opbevaringsalder på 3 år. Det betyder, at elementer, der er 3 år eller ældre, flyttes til arkivpostkassen.

6. Klik **på Ja** for at lukke advarslen og starte processen med at aktivere arkivpostkassen for hver markeret postkasse.

7. Klik på Opdater opdatering, når processen **er** ![fuldført.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) for at opdatere listen på **Arkivsiden** .

    Arkivpostkassen er aktiveret for alle brugere i organisationen.

    ![Listen over postkasser med arkivpostkassen aktiveret.](../media/61a7cb97-1bed-4808-aa5f-b6b761cfa8de.png)

## <a name="step-2-create-new-retention-tags-for-the-archive-and-deletion-policies"></a>Trin 2: Opret nye opbevaringsmærker for arkiverings- og sletningspolitikker

I dette trin skal du oprette de tre brugerdefinerede opbevaringsmærker, der er blevet beskrevet tidligere.
  
- Alpine House 3-årigt Flyt til Arkiv (brugerdefineret arkiveringspolitik)

- Alpine House 7-årigt Slet permanent (brugerdefineret sletningspolitik)

- Alpine House Slettede Elementer, 5 år, Slet og Tillad gendannelse (brugerdefineret mærke til mappen Slettet post)

Hvis du vil oprette nye opbevaringsmærker, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> i din Exchange Online organisation. Sørg for at bruge den klassiske version af EAC.
  
1. Gå til og [https://admin.protection.outlook.com/ecp/](https://admin.protection.outlook.com/ecp/) log på ved hjælp af dine legitimationsoplysninger.
  
2. I EAC skal du gå til **OverholdelsesstyringRetering-tags**  > 

    Der vises en liste over opbevaringsmærker for organisationen.

### <a name="create-a-custom-archive-default-policy-tag"></a>Opret et brugerdefineret arkiveringsstandardpolitikmærke
  
Først skal du oprette et brugerdefineret arkiveringsstandardpolitikmærke (DPT), der flytter elementer til arkivpostkassen efter 3 år.
  
1. På **opbevaringsmærkerne** skal du **klikke på Nyt mærkeNyt**![ ikon og](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) derefter vælge **Anvendt automatisk på hele postkassen (standard)**.

2. På nyt **mærke, der anvendes automatisk på hele postkassen (standard)** udfylder du følgende felter: 

    ![Indstillinger at oprette et nyt arkiveringsstandardpolitikmærke.](../media/41c0a43c-9c72-44e0-8947-da0831896432.png)
  
   1. **Navn** Skriv et navn til det nye opbevaringsmærke. 

   2. **Opbevaringshandling** Vælg **Flyt til Arkiv** for at flytte elementer til arkivpostkassen, når en opbevaringsperiode udløber.

   3. **Opbevaringsperiode** Vælg **Når elementet når følgende alder (i dage)** og angiv derefter varigheden af en opbevaringsperiode. I dette scenarie flyttes elementer til arkivpostkassen efter 1095 dage (3 år).

   4. **Kommentar** (Valgfrit) Skriv en kommentar, der forklarer formålet med det brugerdefinerede opbevaringsmærke.

3. Klik **på Gem** for at oprette det brugerdefinerede arkiv DPT.

    Det nye arkiv DPT vises på listen over opbevaringsmærker.

### <a name="create-a-custom-deletion-default-policy-tag"></a>Opret et brugerdefineret sletningsstandardpolitikmærke
  
Derefter skal du oprette et andet brugerdefineret DPT, men denne vil være en politik for sletning, der sletter elementer permanent efter 7 år.
  
1. På **opbevaringsmærkerne** skal du **klikke på Nyt mærkeNyt**![ ikon og](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) derefter vælge **Anvendt automatisk på hele postkassen (standard)**.

2. På nyt **mærke, der anvendes automatisk på hele postkassen (standard)** udfylder du følgende felter: 

    ![Indstillinger at oprette et nyt standardmærke til sletning.](../media/f1f0ff62-eec9-4824-8e7c-d93dcfb09a79.png)
  
   1. **Navn** Skriv et navn til det nye opbevaringsmærke. 

   2. **Opbevaringshandling** Vælg **Slet permanent for** at fjerne elementer fra postkassen, når en opbevaringsperiode udløber.

   3. **Opbevaringsperiode** Vælg **Når elementet når følgende alder (i dage)** og angiv derefter varigheden af en opbevaringsperiode. I dette scenarie vil elementer blive slettet efter 2555 dage (7 år).

   4. **Kommentar** (Valgfrit) Skriv en kommentar, der forklarer formålet med det brugerdefinerede opbevaringsmærke. 

3. Klik **på Gem** for at oprette det brugerdefinerede DPT. 

    Det nye sletnings-DPT vises på listen over opbevaringsmærker.

### <a name="create-a-custom-retention-policy-tag-for-the-deleted-items-folder"></a>Opret et brugerdefineret mærke til opbevaringspolitikken for mappen Slettet post
  
Det sidste opbevaringsmærke, du skal oprette, er et brugerdefineret opbevaringspolitikmærke (RPT) til mappen Slettet post. Dette mærke sletter elementer i mappen Slettet post efter 5 år og giver en gendannelsesperiode, hvor brugerne kan bruge værktøjet Gendan slettede elementer til at gendanne et element.
  
1. På **Opbevaringsmærkerne** skal du **klikke på Nyt mærke** ![Nyt ikon](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) og derefter vælge **Anvendt automatisk på en standardmappe**.

2. På det **Nye mærke, der anvendes automatisk på en standardmappeside** , skal du udfylde følgende felter:

    ![Indstillinger til at oprette et nyt mærke til opbevaringspolitikken for mappen Slettet post.](../media/6f3104bd-5edb-48ac-884d-5fe13d81dd1d.png)
  
   1. **Navn** Skriv et navn til det nye opbevaringsmærke. 

   2. **Anvend dette mærke på følgende standardmappe** Vælg Slettet post på **rullelisten**.

   3. **Opbevaringshandling** Vælg **Slet og tillad gendannelse** for at slette elementer, når en opbevaringsperiode udløber, men tillad brugere at gendanne et slettet element inden for opbevaringsperioden (der som standard er 14 dage).

   4. **Opbevaringsperiode** Vælg **Når elementet når følgende alder (i dage)** og angiv derefter varigheden af en opbevaringsperiode. I dette scenarie slettes elementer efter 1825 dage (5 år).

   5. **Kommentar** (Valgfrit) Skriv en kommentar, der forklarer formålet med det brugerdefinerede opbevaringsmærke. 

3. Klik **på** Gem for at oprette det brugerdefinerede RPT til mappen Slettet post.

    Det nye RPT vises på listen over opbevaringsmærker.

## <a name="step-3-create-a-new-retention-policy"></a>Trin 3: Opret en ny opbevaringspolitik

Når du har oprettet de brugerdefinerede opbevaringsmærker, er næste trin at oprette en ny opbevaringspolitik og tilføje opbevaringsmærkerne. Du tilføjer de tre brugerdefinerede opbevaringsmærker, du oprettede i trin 2, og de indbyggede mærker, der er nævnt i den første sektion. I trin 4 skal du tildele denne nye opbevaringspolitik til brugerpostkasser.
  
1. I EAC skal du gå til **OverholdelsesstyringReteringspolitikker** > .

2. Klik på **Nyt ikon** for Ny på **siden Opbevaringspolitikker**![](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

3. Skriv et **navn** til den nye opbevaringspolitik i feltet Navn. Eksempelvis Alpine **House Arkiverings- og sletningspolitik**.

4. Klik **på Tilføj nyt** ikon **under Opbevaringsmærker**![](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif).

    Der vises en liste over opbevaringsmærker i organisationen. Bemærk, at de brugerdefinerede mærker, du oprettede i trin 2, vises.

5. Tilføj de 9 opbevaringsmærker, der er fremhævet på følgende skærmbillede (disse mærker er beskrevet mere detaljeret i [afsnittet Flere](#more-information) oplysninger). Hvis du vil tilføje et opbevaringsmærke, skal du markere det og derefter klikke på **Tilføj**.

    ![Føj opbevaringsmærker til den nye opbevaringspolitik.](../media/d8e87176-0716-4238-9e6a-7c4af35541dc.png)
  
    > [!TIP]
    > Du kan markere flere opbevaringsmærker ved at holde **Ctrl nede** og derefter klikke på hvert mærke. 
  
6. Når du har tilføjet opbevaringsmærkerne, skal du klikke på **OK**.

7. På siden **Ny opbevaringspolitik skal** du klikke på **Gem for** at oprette den nye politik.

    Den nye opbevaringspolitik vises på listen. Markér den for at få vist de opbevaringsmærker, der er knyttet til den, i detaljeruden.

    ![Den nye opbevaringspolitik og listen over sammenkædede opbevaringsmærker.](../media/63bc45e6-110b-4dc9-a85f-8eb1961a8258.png)
  
## <a name="step-4-assign-the-new-retention-policy-to-user-mailboxes"></a>Trin 4: Tildel den nye opbevaringspolitik til brugerpostkasser

Når der oprettes en ny postkasse, tildeles den som standard en opbevaringspolitik med navnet Standard MRM-politik. I dette trin skal du erstatte denne opbevaringspolitik (da en postkasse kun kan have én opbevaringspolitik tildelt) ved at tildele den nye opbevaringspolitik, som du oprettede i trin 3, til brugerpostkasserne i organisationen. Dette trin forudsætter, at du tildeler den nye politik til alle postkasser i organisationen.
  
1. I EAC skal du gå **til RecipientsMailboxes** > .

    Der vises en liste over alle brugerpostkasser i organisationen.

2. Markér alle postkasserne ved at klikke på den første på listen, holde **Skift** nede og derefter klikke på den sidste på listen. 

3. I detaljeruden i højre side af EAC under Masseredigering **skal du klikke på** **Flere indstillinger**.

4. Klik **på Opdater** under **Opbevaringspolitik**.

5. På siden **Massetildel** opbevaringspolitik skal du på  rullelisten Vælg opbevaringspolitik vælge den opbevaringspolitik, du oprettede i trin 3. Alpine House arkiv **- og opbevaringspolitik**.

6. Klik **på Gem** for at gemme den nye tildeling af opbevaringspolitik.

7. Hvis du vil bekræfte, at den nye opbevaringspolitik blev tildelt postkasser, kan du gøre følgende:

   1. Vælg en postkasse på siden **Postkasser** , og klik derefter på **Rediger** ![Rediger](../media/d7dc7e5f-17a1-4eb9-b42d-487db59e2e21.png).

   2. Klik på Postkassefunktioner på siden med egenskaber for postkassen for **den valgte bruger**.

   Navnet på den nye politik, der er tildelt postkassen, vises på **rullelisten** Opbevaringspolitik.

## <a name="optional-step-5-run-the-managed-folder-assistant-to-apply-the-new-settings"></a>(Valgfrit) Trin 5: Kør Administreret mappeassistent for at anvende de nye indstillinger

Når du har anvendt den nye opbevaringspolitik på postkasser i trin 4, kan det tage op til 7 dage Exchange Online, før de nye opbevaringsindstillinger anvendes på postkasserne. Dette skyldes, at en proces kaldet *Administreret mappeassistent* behandler postkasser mindst én gang hver 7. dag. I stedet for at vente på at den administrerede mappeassistent kører, kan du gennemtvinge dette ved at køre **Start-ManagedFolderAssistant** cmdlet Exchange Online PowerShell.

 **Hvad sker der, når du kører En administreret mappeassistent?** Den anvender indstillingerne i opbevaringspolitikken ved at undersøge elementer i postkassen og afgør, om de er underlagt opbevaring. Den stempler derefter elementer underlagt opbevaring med det relevante opbevaringsmærke, og tager derefter den angivne opbevaringshandling på elementer der er over opbevaringsalderen.
  
Her er trinnene til at oprette forbindelse til Exchange Online PowerShell og derefter køre Administreret mappeassistent på hver postkasse i organisationen.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. Kør følgende to kommandoer for at starte Administreret mappeassistent for alle brugerpostkasser i organisationen.

    ```powershell
    $Mailboxes = Get-Mailbox -ResultSize Unlimited -Filter {RecipientTypeDetails -eq "UserMailbox"}
    ```

    ```powershell
    $Mailboxes.Identity | Start-ManagedFolderAssistant
    ```

Det var det! Du har konfigureret en arkiverings- og sletningspolitik for Alpine House organisationen.

> [!NOTE]
> Som tidligere nævnt behandler Administreret mappeassistent postkasser mindst én gang hver 7. dag. Så det er muligt, at en postkasse kan behandles oftere af den administrerede mappeassistent. Administratorer kan heller ikke forudsige næste gang, en postkasse behandles af administreret mappeassistent, hvilket er en af grundene til, at du muligvis vil køre den manuelt. Men hvis du midlertidigt vil forhindre Administreret mappeassistent i at anvende de nye opbevaringsindstillinger på en postkasse, `Set-Mailbox -ElcProcessingDisabled $true` kan du køre kommandoen for midlertidigt at deaktivere Administreret mappeassistent i at behandle en postkasse. Kør kommandoen for at genaktivere Administreret mappeassistent for en `Set-Mailbox -ElcProcessingDisabled $false` postkasse. Hvis en postkassebruger har en deaktiveret konto, behandler vi ikke flytningselementer til arkiveringshandlingen for den pågældende postkasse.
  
## <a name="optional-step-6-make-the-new-retention-policy-the-default-for-your-organization"></a>(Valgfrit) Trin 6: Gør den nye opbevaringspolitik til standard for organisationen

I trin 4 skal du tildele den nye opbevaringspolitik til eksisterende postkasser. Men du kan konfigurere Exchange Online så den nye opbevaringspolitik tildeles nye postkasser, der oprettes i fremtiden. Det gør du ved Exchange Online PowerShell til at opdatere din organisations standardpostkasseplan. En *postkasseplan* er en skabelon, der automatisk konfigurerer egenskaber for nye postkasser.  I dette valgfrie trin kan du erstatte den aktuelle opbevaringspolitik, der er tildelt til postkasseplanen (som standard MRM Standardpolitik) med den opbevaringspolitik, du oprettede i trin 3. Når du har opdateret postkasseplanen, tildeles den nye opbevaringspolitik til nye postkasser.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør følgende kommando for at få vist oplysninger om postkasseplaner i organisationen.

    ```powershell
    Get-MailboxPlan | Format-Table DisplayName,RetentionPolicy,IsDefault
    ```

    Bemærk den postkasseplan, der er angivet som standard.

3. Kør følgende kommando for at tildele den nye opbevaringspolitik, du oprettede i trin 3 (f.eks **Alpine House** Arkiv- og Opbevaringspolitik) til standardpostkassens plan. I dette eksempel antages det, at navnet på standardpostkassens plan **er ExchangeOnlineEnterprise**.

    ```powershell
    Set-MailboxPlan "ExchangeOnlineEnterprise" -RetentionPolicy "Alpine House Archive and Retention Policy"
    ```

4. Du kan køre kommandoen igen i trin 2 for at bekræfte, at den opbevaringspolitik, der er tildelt standardpostkassens plan, er blevet ændret.

## <a name="more-information"></a>Flere oplysninger

- Hvordan beregnes opbevaringsalder? Opbevaringsalderen for postkasseelementer beregnes fra leveringsdatoen eller oprettelsesdatoen for elementer som f.eks. kladdemeddelelser, der ikke er sendt, men som oprettes af brugeren. Når administreret mappeassistent behandler elementer i en postkasse, stempler den en startdato og en udløbsdato for alle elementer, der har opbevaringsmærker med opbevaringshandlingen Slet og Tillad gendannelse eller Slet permanent. Elementer, der har et arkivmærke, er stemplet med en flyttedato. 

- Den følgende tabel indeholder flere oplysninger om hvert opbevaringsmærke, der er føjet til den brugerdefinerede opbevaringspolitik, der blev oprettet ved at følge trinnene i dette emne.

    | Opbevaringsmærke | Hvad dette mærke gør | Indbygget eller brugerdefineret? | Type |
    |:-----|:-----|:-----|:-----|
    |Alpine House 3-årigt Flyt til Arkiv  <br/> |Flytter elementer, der er 1095 dage (3 år) gamle, til arkivpostkassen.  <br/> |Brugerdefineret (Se [Trin 2: Opret nye opbevaringsmærker for arkiverings- og sletningspolitikker](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Standardpolitikmærke (arkiv); dette mærke anvendes automatisk på hele postkassen.  <br/> |
    |Alpine House 7 år Slet permanent  <br/> |Elementer i den primære postkasse eller arkivpostkassen slettes permanent, når de er 7 år gamle.  <br/> |Brugerdefineret (Se [Trin 2: Opret nye opbevaringsmærker for arkiverings- og sletningspolitikker](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Standardpolitikmærke (sletning). dette mærke anvendes automatisk på hele postkassen.  <br/> |
    |Alpine House Slettede Elementer 5 år Slet og Tillad gendannelse  <br/> |Sletter elementer fra mappen Slettet post, der er 5 år gamle. Brugere kan gendanne disse elementer op til 14 dage, efter de er blevet slettet.<sup>\*</sup> <br/> |Brugerdefineret (Se [Trin 2: Opret nye opbevaringsmærker for arkiverings- og sletningspolitikker](#step-2-create-new-retention-tags-for-the-archive-and-deletion-policies))  <br/> |Opbevaringspolitikmærke (Slettede elementer); dette mærke anvendes automatisk på elementer i mappen Slettet post.  <br/> |
    |Genoprettelige elementer 14 dage Flyt til Arkiv  <br/> |Flytter elementer, der har været i mappen Genoprettelige elementer i 14 dage, til mappen Genoprettelige elementer i arkivpostkassen.  <br/> |Indbygget  <br/> |Opbevaringspolitikmærke (genoprettelige elementer); dette mærke anvendes automatisk på elementer i mappen Genoprettelige elementer.  <br/> |
    |Uønsket mail  <br/> |Elementer, der har været i mappen Uønsket mail i 30 dage, slettes permanent. Brugere kan gendanne disse elementer op til 14 dage, efter de er blevet slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Opbevaringspolitikmærke (uønsket mail); dette mærke anvendes automatisk på elementer i mappen Uønsket mail.  <br/> |
    |1 Måned Slet  <br/> |Elementer, der er 30 dage gamle, slettes permanent. Brugere kan gendanne disse elementer op til 14 dage, efter de er blevet slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |1 År Slet  <br/> |Elementer, der er 365 dage gamle, slettes permanent. Brugere kan gendanne disse elementer op til 14 dage, efter de er blevet slettet.<sup>\*</sup> <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |Slet aldrig  <br/> |Dette mærke forhindrer elementer i at blive slettet af en opbevaringspolitik.  <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |
    |Personlig 1 år flyt til arkiv  <br/> |Flytter elementer til arkivpostkassen efter 1 år.  <br/> |Indbygget  <br/> |Personlig; dette mærke kan anvendes af brugere.  <br/> |

    > <sup>\*</sup>Brugerne kan bruge værktøjet Gendan slettede elementer i Outlook og Outlook på internettet (tidligere kaldet Outlook Web App) til at gendanne et slettet element inden for opbevaringsperioden for slettede elementer, der som standard er 14 dage Exchange Online. En administrator kan bruge Windows PowerShell til at øge opbevaringsperioden for slettede elementer til maksimalt 30 dage. Få mere at vide under: Gendan slettede elementer [i Outlook for Windows](https://support.office.com/article/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce) og Skift opbevaringsperioden for slettede elementer for en postkasse [Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/change-deleted-item-retention)
  
- Brug af **mærket Genoprettelige elementer 14** dage Flyt til arkiv-opbevaring hjælper med at frigøre lagerplads i mappen Genoprettelige elementer i brugerens primære postkasse. Dette er nyttigt, når en brugers postkasse er sat i venteposition, hvilket betyder, at intet nogensinde er blevet slettet permanent i brugerens postkasse. Uden at flytte elementer til arkivpostkassen er det muligt, at lagerkvoten for mappen Genoprettelige elementer i den primære postkasse nås. Du kan finde flere oplysninger om dette, og hvordan du undgår dette, i Øg kvoten for genoprettelige elementer [for postkasser i venteposition](./increase-the-recoverable-quota-for-mailboxes-on-hold.md).
