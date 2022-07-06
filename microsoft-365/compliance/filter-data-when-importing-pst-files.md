---
title: Filtrer data ved import af PST-filer
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du filtrerer data ved hjælp af funktionen til intelligent import i Microsoft 365-importtjenesten, når du importerer PST-filer til Microsoft 365.
ms.openlocfilehash: 1a9483d77ff575b643d4ab9717d286b608bea35d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640066"
---
# <a name="filter-data-when-importing-pst-files"></a>Filtrer data ved import af PST-filer

Brug den nye funktion Intelligent import i tjenesten Microsoft 365 Import til at filtrere de elementer i PST-filer, der rent faktisk importeres til destinationspostkasserne. Sådan fungerer det:
  
- Når du har oprettet og sendt et PST-importjob, uploades PST-filer til et Azure-lagerområde i Microsoft-cloudmiljøet.
  
- Microsoft 365 analyserer dataene i PST-filerne på en sikker og sikker måde ved at identificere alderen på postkasseelementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne.
  
- Når analysen er fuldført, og dataene er klar til at blive importeret, har du mulighed for at importere alle data i PST-filerne, som de er, eller trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres. Du kan f.eks. vælge at:
  
  - Importér kun elementer med en bestemt alder.
  
  - Importér de valgte meddelelsestyper.
  
  - Udelad meddelelser, der er sendt eller modtaget af bestemte personer.
  
- Når du har konfigureret filterindstillingerne, importerer Microsoft 365 kun de data, der opfylder filtreringskriterierne, til de destinationspostkasser, der er angivet i importjobbet.
  
I følgende grafik vises processen intelligent import, og de opgaver, du udfører, og de opgaver, der udføres af Office 365, fremhæves.
  
![Processen Intelligent import i Office 365.](../media/f2ec309b-11f5-48f2-939c-a6ff72152d14.png)
  
## <a name="create-a-pst-import-job"></a>Opret et PST-importjob

- Trinnene i dette emne forudsætter, at du har oprettet et PST-importjob i tjenesten Office 365 Importér ved hjælp af netværksupload eller drevforsendelse. Du kan finde en trinvis vejledning i et af følgende emner:
    
  - [Brug netværksoverførsel til at importere PST-filer til Office 365](use-network-upload-to-import-pst-files.md)
    
  - [Brug drevforsendelse til at importere PST-filer til Office 365](use-drive-shipping-to-import-pst-files-to-office-365.md)
    
- Når du har oprettet et importjob ved hjælp af netværksupload, angives status for importjobbet på siden Import i Security & Compliance Center til **Igangværende analyse**, hvilket betyder, at Microsoft 365 analyserer dataene i de PST-filer, du har uploadet. Klik på **Opdater**![opdatering.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) for at opdatere status for importjobbet. 
    
- I forbindelse med import af drevforsendelser analyseres dataene af Microsoft 365, når Microsofts datacenterpersonale modtager din harddisk og uploader PST-filerne til Azure-lagerområdet for din organisation.
  
## <a name="filter-data-that-gets-imported-to-mailboxes"></a>Filtrer data, der importeres til postkasser

Når du har oprettet et PST-importjob, skal du følge disse trin for at filtrere dataene, før du importerer dem til Office 365.
  
1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, og log på med legitimationsoplysningerne for en administratorkonto i din organisation.
    
2. Klik på **Import** af **datalivscyklusstyring** \> i ruden til venstre på overholdelsesportalen.
    
    Importjob for din organisation vises under fanen **Importér** . Værdien **Analyse fuldført** i kolonnen **Status** angiver de importjob, der er analyseret af Microsoft 365 og er klar til at blive importeret.
    
    ![Status for fuldført analyse angiver, at Microsoft 365 har analyseret dataene i PST-filer.](../media/de5294f4-f0ba-4b92-a48a-a4b32b6da490.png)
  
3. Vælg det importjob, du vil fuldføre, og klik på **Importér for at Office 365**.
  
    Der vises en fly out-side med oplysninger om PST-filerne og andre oplysninger om importjobbet.

4. Klik på **Importér for at Office 365**.
    
    Siden **Filtrer dine data** vises. Den indeholder dataindsigt om dataene i PST-filerne for importjobbet, herunder oplysninger om dataenes alder. 
    
    ![På siden Filtrer dine data vises dataindsigt for PST-filerne for importjobbet.](../media/3b537ec0-25a4-45a4-96d5-a429e2a33128.png)
  
5. Afhængigt af om du vil trimme de data, der er importeret til Microsoft 365, skal du gøre et af følgende under **Vil du filtrere dine data?**
  
    a. Klik på **Ja. Jeg vil filtrere den, før jeg importerer** , for at trimme de data, du importerer, og klik derefter på **Næste**.
  
    Siden **Importér data til Office 365 side** vises med detaljeret dataindsigt fra den analyse, som Microsoft 365 udførte. 
  
    ![Microsoft 365 viser detaljeret dataindsigt fra analysen af PST-filerne.](../media/4881205f-0288-4c32-a440-37e2160295f2.png)
  
    Grafen på denne side viser mængden af data, der importeres. Oplysninger om hver meddelelsestype, der findes i PST-filerne, vises i diagrammet. Du kan holde markøren over hver søjle for at få vist bestemte oplysninger om den pågældende meddelelsestype. Der er også en rulleliste med forskellige aldersværdier baseret på analysen af PST-filerne. Når du vælger en alder på rullelisten, opdateres grafen for at vise, hvor mange data der importeres for den valgte alder. 
  
    b. Hvis du vil konfigurere tilføjelsesfiltre for at reducere mængden af importerede data, skal du klikke på **Flere filtreringsindstillinger**.
  
    ![Konfigurer filtrene på siden Flere indstillinger for at trimme de data, der importeres.](../media/3f8d68c3-3fe2-4b4e-9488-b368b98fa9fe.png)
  
    Du kan konfigurere disse filtre:
  
      - **Alder** – Vælg en alder, så det kun er elementer, der er nyere end den angivne alder, der importeres. Se afsnittet [Flere oplysninger](#more-information) for at få en beskrivelse af, hvordan Microsoft 365 bestemmer alders buckets for filteret **Alder** . 
  
      - **Type** – I dette afsnit vises alle de meddelelsestyper, der blev fundet i PST-filerne til importjobbet. Du kan fjerne markeringen i et afkrydsningsfelt ud for en meddelelsestype, som du vil udelade. Du kan ikke udelade meddelelsestypen Andet. Se afsnittet [Flere oplysninger](#more-information) for at få en liste over postkasseelementer, der er inkluderet i kategorien Andet.
  
      - **Brugere** – Du kan udelade meddelelser, der sendes eller modtages af bestemte personer. Hvis du vil udelade personer, der vises i feltet Fra: , til: eller feltet Cc: i meddelelser, skal du klikke på **Udelad brugere** ud for den pågældende modtagertype. Skriv mailadressen (SMTP-adressen) for personen, og klik på **Ikonet Tilføj**![ny.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) for at føje dem til listen over udeladte brugere for den pågældende modtagertype og derefter klikke på **Gem** for at gemme listen over udeladte brugere. 
  
        > [!NOTE]
        > Microsoft 365 viser ikke dataindsigt, der er resultatet af indstillingen af filteret **Personer** . Men hvis du angiver dette filter til at udelade meddelelser, der er sendt eller modtaget af bestemte personer, udelades disse meddelelser under den faktiske importproces. 
  
    c. Klik på **Anvend** på siden **Flere filtreringsindstillinger** for at gemme dine filterindstillinger. 
  
    Dataindsigten på siden **Importér data til Office 365** opdateres på baggrund af dine filterindstillinger, herunder den samlede mængde data, der importeres på baggrund af filterindstillingerne. Der vises også en oversigt over filterindstillingerne. Du kan klikke på **Rediger** ud for et filter for at ændre indstillingen, hvis det er nødvendigt. 
  
    ![Dataindsigten opdateres på baggrund af dine filterindstillinger.](../media/897e20fb-3b13-44c3-9d56-9f330750f2a3.png)
  
    d. Klik på **Næste**.
  
    Der vises en statusside, der viser dine filterindstillinger. Igen kan du redigere en af filterindstillingerne.
  
    e. Klik på **Importér data** for at starte importen. Den samlede mængde data, der importeres, vises. 
  
    Eller
  
    a. Klik på **Nej, jeg vil importere alt** for at importere alle data i PST-filerne til Office 365, og klik derefter på **Næste**.
  
    b. Klik på **Importér data** på siden **Importér data til Office 365** for at starte importen. Den samlede mængde data, der importeres, vises. 
  
6. Klik på **Opdater** ![opdatering under fanen **Importér**.](../media/165fb3ad-38a8-4dd9-9e76-296aefd96334.png) Status for importjobbet vises i kolonnen **Status** .
  
7. Klik på importér jobbet for at få vist mere detaljerede oplysninger, f.eks. status for hver PST-fil og de filterindstillinger, du har konfigureret.

## <a name="more-information"></a>Flere oplysninger

- Hvordan bestemmer Microsoft 365 intervaller for aldersfilteret? Når Microsoft 365 analyserer en PST-fil, kigger den på det sendte eller modtagne tidsstempel for hvert element (hvis et element har både et sendt og modtaget tidsstempel, vælges den ældste dato). Derefter kigger Microsoft 365 på årsværdien for dette tidsstempel og sammenligner den med den aktuelle dato for at bestemme elementets alder. Disse aldre bruges derefter som værdier på rullelisten for filteret **Alder** . Hvis en PST-fil f.eks. indeholder meddelelser fra 2016, 2015 og 2014, vil værdierne i filteret **Alder** være **1 år**, **2 år** og **3 år**.
  
- I følgende tabel vises de meddelelsestyper, der er inkluderet i kategorien **Andet** i filteret **Type** på siden **Flere indstillinger** (se Trin 5b i den forrige procedure). I øjeblikket kan du ikke udelade elementer i kategorien "Andet", når du importerer psts til Office 365. 
  
    |**Meddelelsesklasse-id**|**Postkasseelementer, der bruger denne meddelelsesklasse**|
    |:-----|:-----|
    |IPM. Aktivitet  <br/> |Journaloptegnelser  <br/> |
    |IPM. Dokument  <br/> |Dokumenter og filer (ikke knyttet til en mail)  <br/> |
    |IPM. Fil  <br/> |(samme som IPM. Dokument)  <br/> |
    |IPM. Note.IMC.Notification  <br/> |Rapporter, der sendes af Internet Mail Connect, som er den Exchange Server gateway til internettet  <br/> |
    |IPM. Note.Microsoft.Fax  <br/> |Faxmeddelelser  <br/> |
    |IPM. Note.Rules.Oof.Template.Microsoft  <br/> |Autosvar fraværende-meddelelser  <br/> |
    |IPM. Note.Rules.ReplyTemplate.Microsoft  <br/> |Svar, der er sendt af en indbakkeregel  <br/> |
    |IPM. OLE. Klasse  <br/> |Undtagelser for en tilbagevendende serie  <br/> |
    |IPM. Recall.Report  <br/> |Rapporter til tilbagekaldelse af meddelelser  <br/> |
    |IPM. Fjernbetjening  <br/> |Fjernmailmeddelelser  <br/> |
    |IPM. Rapport  <br/> |Rapporter over elementstatus  <br/> |
