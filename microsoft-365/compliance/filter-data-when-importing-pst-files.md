---
title: Filtrer data, når du importerer PST-filer
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 26af16df-34cd-4f4a-b893-bc1d2e74039e
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Få mere at vide om, hvordan du filtrerer data ved hjælp af den intelligente importfunktion Microsoft 365 importtjenesten, når du importerer PST-filer Microsoft 365.
ms.openlocfilehash: 593ce847803fdc3529fbe9276721e6bb8cf79069
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63587493"
---
# <a name="filter-data-when-importing-pst-files"></a>Filtrer data, når du importerer PST-filer

Brug den nye intelligente importfunktion i Microsoft 365 Import-tjenesten til at filtrere de elementer i PST-filer, der faktisk importeres til målpostkasserne. Sådan fungerer det:
  
- Når du har oprettet og indsendt et PST-importjob, uploades PST-filer til et Azure-lagringsområde i Microsoft-skyen.
  
- Microsoft 365 analyserer dataene i PST-filerne på en sikker måde ved at identificere alderen på postkasseelementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne.
  
- Når analysen er færdig, og dataene er klar til at blive importeret, har du mulighed for at importere alle data i PST-filerne, som de er, eller trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres. Du kan f.eks. vælge at:
  
  - Importér kun elementer med en bestemt alder.
  
  - Importér markerede meddelelsestyper.
  
  - Udelad meddelelser, der er sendt eller modtaget af bestemte personer.
  
- Når du har konfigureret filterindstillingerne, Microsoft 365 kun de data, der opfylder filterkriterierne, til de målpostkasser, der er angivet i importjobbet.
  
Følgende grafik viser den intelligente importproces og fremhæver de opgaver, du udfører, og de opgaver, der udføres Office 365.
  
![Den intelligente importproces i Office 365.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>Opret et PST-importjob

- Trinnene i dette emne forudsætter, at du har oprettet et PST-importjob i Office 365 importtjenesten ved hjælp af netværksupload eller drevforsendelse. Du kan finde en trinvis vejledning under et af følgende emner:
    
  - [Brug netværksupload til at importere PST-filer Office 365](use-network-upload-to-import-pst-files.md)
    
  - [Brug drevforsendelse til at importere PST-filer til Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Når du har oprettet et importjob ved hjælp af netværksoverførsel, angives status for importjobbet på siden Import i Security & Compliance Center til Analyse, der er i **gang, hvilket** betyder, at Microsoft 365 analyserer dataene i de PST-filer, du har uploadet. Klik **på Refreshrefresh**![.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) for at opdatere status for importjobbet. 
    
- For importjob til drevforsendelse analyseres dataene af Microsoft 365, når en medarbejder i Microsofts datacenter har modtaget din harddisk og uploadet PST-filerne til Azure-lagringsområdet for organisationen.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Filtrere data, der importeres til postkasser

Når du har oprettet et PST-importjob, skal du følge disse trin for at filtrere dataene, før du importerer dem Office 365.
  
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter og</a> log på med legitimationsoplysningerne for en administratorkonto i organisationen.
    
2. Klik på Importér Microsoft 365 Overholdelsescenter venstre  \> **rude.**
    
    Importjobs for din organisation er angivet på **fanen** Importér. Værdien **Udført analyse** i kolonnen **Status** angiver de importjob, der er blevet analyseret af Microsoft 365 og er klar til at blive importeret.
    
    ![Status for analyse fuldført indikerer, Microsoft 365 har analyseret dataene i PST-filer.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Vælg det importjob, du vil fuldføre, og klik på **Importér til Office 365**.
  
    En side med flyv ud vises med oplysninger om PST-filer og andre oplysninger om importjobbet.

4. Klik **på Importér for Office 365**.
    
    Siden **Filtrer** dine data vises. Den indeholder dataindsigt om dataene i PST-filerne til importjobbet, herunder oplysninger om alderen på dataene. 
    
    ![På siden Filtrer dine data vises dataindsigt om PST-filerne for importjobbet.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. Afhængigt af, om du vil trimme de data, der importeres Microsoft 365, skal du gøre et af følgende under Vil du filtrere dine **data**?:
  
    a. Klik **på Ja, jeg vil filtrere dem, før du importerer for** at trimme de data, du importerer, og klik derefter på **Næste**.
  
    Siden **Importér data Office 365 en** side vises med detaljeret dataindsigt fra den analyse, Microsoft 365 udført. 
  
    ![Microsoft 365 viser detaljeret dataindsigt fra dens analyse af PST-filerne.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Grafen på denne side viser mængden af data, der skal importeres. Oplysninger om hver meddelelsestype, der findes i PST-filerne, vises i grafen. Du kan holde markøren over hver linje for at få vist specifikke oplysninger om den pågældende meddelelsestype. Der findes også en rulleliste med forskellige aldersværdier, der er baseret på analyse af PST-filerne. Når du vælger en alder på rullelisten, opdateres grafen for at vise, hvor mange data der importeres for den valgte alder. 
  
    b. Klik på Flere filtreringsindstillinger for at konfigurere tilføjelsesfiltre for at reducere mængden af importerede **data**.
  
    ![Konfigurer filtrene på siden Flere indstillinger for at trimme de importerede data.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Du kan konfigurere disse filtre:
  
      - **Alder** – Vælg en alder, så kun elementer, der er nyere end den angivne alder, importeres. Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af, Microsoft 365 bestemmer alders-buckets for **aldersfilteret**. 
  
      - **Type** – Dette afsnit viser alle de meddelelsestyper, der blev fundet i PST-filerne til importjobbet. Du kan fjerne markeringen i et felt ud for en meddelelsestype, som ikke skal udelades. Du kan ikke udelade meddelelsestypen Andet. Se afsnittet [Flere oplysninger](#more-information) for at få en liste over postkasseelementer, der er inkluderet i kategorien Andet.
  
      - **Brugere** – Du kan udelade meddelelser, der sendes eller modtages af bestemte personer. Hvis du vil udelade personer, der vises i feltet Fra:, Til:, eller feltet Cc:, i meddelelser, skal du klikke på Udelad **brugere ud for** den pågældende modtagertype. Skriv mailadressen (SMTP-adresse) på personen, og klik **på Ikonet**![ Tilføj Ny.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) for at føje dem til listen over ekskluderede brugere for den pågældende modtagertype, og klik derefter på **Gem** for at gemme listen over ekskluderede brugere. 
  
        > [!NOTE]
        > Microsoft 365 ikke dataindsigt, der er resultatet af indstillingen af **filteret** Personer. Men hvis du indstiller dette filter til at udelade meddelelser, der sendes eller modtages af bestemte personer, udelades disse meddelelser under den faktiske import. 
  
    c. Klik **på** Anvend på **siden Flere filtreringsindstillinger** for at gemme dine filterindstillinger. 
  
    Dataindsigtene på siden **Importér data til Office 365** opdateres baseret på dine filterindstillinger, herunder den samlede mængde data, der importeres, baseret på filterindstillingerne. Der vises også en oversigt over filterindstillingerne. Du kan klikke på **Rediger ud** for et filter for at ændre indstillingen, hvis det er nødvendigt. 
  
    ![Dataindsigt opdateres baseret på dine filterindstillinger.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. Klik på **Næste**.
  
    Der vises en statusside med dine filterindstillinger. Igen kan du redigere alle filterindstillingerne.
  
    e. Klik **på Importér data** for at starte importen. Den samlede mængde data, der skal importeres, vises. 
  
    Eller
  
    a. Klik **på Nej, jeg vil importere alt for** at importere alle data i PST-filerne til pst Office 365, og klik derefter på **Næste**.
  
    b. På siden **Importér data Office 365** skal du klikke på **Importér data** for at starte importen. Den samlede mængde data, der skal importeres, vises. 
  
6. Klik på **Opdater** opdatering under **fanen** ![Importér](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png). Status for importjobbet vises i kolonnen **Status** .
  
7. Klik på importér jobbet for at få vist mere detaljerede oplysninger, f.eks. status for hver PST-fil og de filterindstillinger, du har konfigureret.

## <a name="more-information"></a>Flere oplysninger

- Hvordan Microsoft 365 intervallerne for aldersfilteret? Når Microsoft 365 analyserer en PST-fil, kigger den på det sendte eller modtagne tidsstempel for hvert element (hvis et element både har et tidsstempel, der er sendt og modtaget, er den ældste dato markeret). Derefter Microsoft 365 på årsværdien for det pågældende tidsstempel og sammenligner den med den aktuelle dato for at bestemme elementets alder. Disse aldre bruges derefter som værdier på rullelisten for filteret **Alder.** Hvis en PST-fil f.eks. indeholder meddelelser fra 2016, 2015 og 2014, så er værdierne **i filteret** Alder **1** år, **2** år og **3 år**.
  
- I følgende tabel vises de meddelelsestyper, der er medtaget i kategorien Andre i **filteret Type** på siden Flere indstillinger (se trin 5b i den forrige procedure).  I øjeblikket kan du ikke udelade elementer i kategorien "Andre", når du importerer PST'er til Office 365. 
  
    |**Meddelelsesklasse-id**|**Postkasseelementer, der bruger denne meddelelsesklasse**|
    |:-----|:-----|
    |IPM. Aktivitet  <br/> |Journalposter  <br/> |
    |IPM. Dokument  <br/> |Dokumenter og filer (ikke vedhæftet en mail)  <br/> |
    |IPM. Filer  <br/> |(samme som IPM. Dokument)  <br/> |
    |IPM. Note.IMC.Notification  <br/> |Rapporter, der sendes af Forbind, som er den Exchange Server gateway til internettet  <br/> |
    |IPM. Note.Microsoft.Fax  <br/> |Faxmeddelelser  <br/> |
    |IPM. Note.Rules.Oof.Template.Microsoft  <br/> |Autoreply-meddelelser (ikke til kontoret)  <br/> |
    |IPM. Note.Rules.ReplyTemplate.Microsoft  <br/> |Svar sendt af en indbakkeregel  <br/> |
    |IPM. OLE. Klasse  <br/> |Undtagelser for en tilbagevendende serie  <br/> |
    |IPM. Recall.Report  <br/> |Tilbagekaldelsesrapporter over meddelelser  <br/> |
    |IPM. Fjernforbindelse  <br/> |Fjernmails  <br/> |
    |IPM. Rapport  <br/> |Statusrapporter for element  <br/> |
