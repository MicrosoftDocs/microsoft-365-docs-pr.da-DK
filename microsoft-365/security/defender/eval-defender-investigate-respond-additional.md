---
title: Prøv Microsoft 365 Defender egenskaber for hændelsesrespons i et pilotmiljø
description: Prøv egenskaber for hændelsesrespons Microsoft 365 Defender at prioritere og administrere hændelser, automatisere undersøgelser og bruge avanceret jagt til trusselsregistrering.
keywords: Microsoft 365 Defender prøveversion kan du prøve Microsoft 365 Defender, evaluere Microsoft 365 Defender, Microsoft 365 Defender evalueringslaboratorium Microsoft 365 Defender  pilot, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 0ad2fc9a1566e7816b3ff806b7d07ac29347cc89
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754780"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Prøv Microsoft 365 Defender egenskaber for hændelsesrespons i et pilotmiljø

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 ud af 2](eval-defender-investigate-respond.md) i en undersøgelse af og reaktion på en hændelse i Microsoft 365 Defender et pilotmiljø. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-investigate-respond.md) .

Når du har udført et [hændelsessvar for en simuleret angreb](eval-defender-investigate-respond-simulate-attack.md), er her nogle Microsoft 365 Defender at udforske:

|Funktion |Beskrivelse |
|:-------|:-----|
| [Prioritering af hændelser](#prioritize-incidents) | Brug filtrering og sortering af køen over hændelser til at afgøre, hvilke hændelser der skal håndteres som det næste. |
| [Administrer hændelser](#manage-incidents) | Rediger hændelsesegenskaber for at sikre korrekt tildeling, tilføje mærker og kommentarer og løse en hændelse. |
| [Automatiseret undersøgelse og svar](#examine-automated-investigation-and-response-with-the-action-center) | Brug automatiserede undersøgelses- og svarfunktioner (AIR) til at hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt. Handlingscenter er en "enkelt rude med glas"-oplevelse for hændelses- og beskedopgaver, f.eks. godkendelse af afventende afhjælpningshandlinger. |
| [Avanceret jagt](#use-advanced-hunting) | Brug forespørgsler til proaktivt at undersøge hændelser i dit netværk og finde trusselsindikatorer og -enheder. Du kan også bruge avanceret jagt under undersøgelsen og afhjælpningen af en hændelse. |


## <a name="prioritize-incidents"></a>Prioriter hændelser

Du kommer til hændelseskøen **fra Hændelser & hændelser > hændelser** i hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Afsnittet om & vigtige beskeder i Microsoft 365 Defender portal" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::


Afsnittet **Seneste hændelser og beskeder** viser en graf over antallet af modtagne beskeder og hændelser, der er oprettet inden for de seneste 24 timer.

Hvis du vil undersøge listen over hændelser og prioritere deres betydning for tildeling og undersøgelse, kan du: 

- Konfigurer brugerdefinerbare kolonner ( **vælg Vælg** kolonner) for at give dig indblik i forskellige egenskaber for hændelsen eller de på påvirkede enheder. På den måde kan du tage en informeret beslutning om prioritering af hændelser til analyse.

- Brug filtrering til at fokusere på et bestemt scenarie eller en bestemt trussel. Anvendelse af filtre på hændelseskøen kan hjælpe med at afgøre, hvilke hændelser der kræver øjeblikkelig handling. 

Fra standardhændelseskøen skal du **vælge Filtre** for **at få vist** ruden Filtre, hvorfra du kan angive et bestemt sæt hændelser. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Ruden Filtre i sektionen & beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Få mere at vide [under Prioriter hændelser](incident-queue.md).

## <a name="manage-incidents"></a>Administrer hændelser

Du kan administrere hændelser fra **ruden Administrer hændelse** for en hændelse. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Ruden Administrer hændelse i sektionen & med beskeder i Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Du kan få vist denne rude **via linket Administrer** hændelse på:

- Ruden Egenskaber for en hændelse i hændelseskøen.
- **Oversigtsside** for en hændelse.

Her er de måder, du kan administrere dine hændelser på:

- Rediger hændelsens navn

  Skift det automatisk tildelte navn baseret på bedste praksis for sikkerhedsteamet.
  
- Tilføje hændelsesmærker

  Tilføj mærker, som dit sikkerhedsteam bruger til at klassificere hændelser, som kan filtreres senere.
  
- Tildel hændelsen

  Tildel det til et brugerkontonavn, som kan filtreres senere.
  
- Løs en hændelse

  Luk hændelsen, når det er blevet løst.
  
- Fastsæt klassificeringen og bestemmelsen

  Klassificer og vælg trusselstypen, når du løser en hændelse.
  
- Tilføj kommentarer

  Brug kommentarer til fremskridt, noter eller andre oplysninger baseret på bedste praksis for dit sikkerhedsteam. Den komplette kommentaroversigt er tilgængelig fra **indstillingen Kommentarer og** historik på detaljesiden for en hændelse.

Få mere at vide under [Administrer hændelser](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>Undersøg automatiseret undersøgelse og svar med Handlingscenter

Afhængigt af hvordan automatiserede undersøgelses- og svarfunktioner er konfigureret for din organisation, udføres afhjælpningshandlinger automatisk eller kun efter godkendelse fra dit sikkerhedsteam. Alle handlinger, uanset om de er ventende eller fuldførte, er angivet i Handlingscenter [, som](m365d-action-center.md) viser ventende og afsluttede afhjælpningshandlinger for dine enheder, mail & samarbejdsindhold og identiteter på ét sted.

Her er et eksempel.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Samlet handlingscenter i Microsoft 365 Defender portalen" lightbox="../../media/m3d-action-center-unified.png":::

Fra Handlingscenter kan du vælge afventende handlinger og derefter godkende eller afvise dem i pop op-ruden. Her er et eksempel.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Ruden, der viser indstillingerne for at godkende eller afvise en handling i Microsoft 365 Defender portal" lightbox="../../media/air-actioncenter-itemselected.png":::


Godkend (eller afvis) afventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fortsætte og afslutte i tide.

Få mere at vide under [Automatiseret undersøgelse og svar](m365d-autoir.md) og [Handlingscenter](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>Brug avanceret jagt

> [!NOTE]
> Før vi hjælper dig gennem den avancerede simulering, kan du se følgende video for at forstå avancerede jagtkoncepter, se, hvor du kan finde den på portalen, og find ud af, hvordan den kan hjælpe dig i dine sikkerhedshandlinger.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


Hvis den [valgfrie filløse](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) PowerShell-angrebssimulering var et rigtigt angreb, der allerede havde nået adgangsfasen for legitimationsoplysninger, kan du når som helst bruge avanceret jagt i undersøgelsen til proaktivt at søge gennem begivenheder og poster i netværket ved hjælp af det, du allerede ved fra de genererede beskeder og berørte enheder. 

Baseret på oplysningerne i [SMB-beskeden (User and IP address reconnaissance),](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) `IdentityDirectoryEvents` kan du f.eks. bruge tabellen til at finde alle SMB-sessionsregistreringshændelser eller finde flere discovery-aktiviteter i forskellige andre protokoller i Microsoft Defender til `IdentityQueryEvents` identitetsdata ved hjælp af tabellen.


### <a name="hunting-environment-requirements"></a>Krav til jagtmiljø

Der kræves en enkelt intern postkasse og enhed til denne simulering. Du skal også bruge en ekstern mailkonto for at sende testmeddelelsen.

1. Kontrollér, at din lejer [har aktiveret Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identificer en destinationspostkasse, der skal bruges til at modtage mails.

   - Denne postkasse skal overvåges af Microsoft Defender for Office 365

   - Enheden fra krav 3 skal have adgang til denne postkasse

3. Konfigurer en testenhed:

    a. Sørg for, at du bruger Windows 10 version 1903 eller nyere version.

    b. Deltag i testenheden til testdomænet.

    c. [Slå Windows Defender Antivirus til](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Hvis du har problemer med at aktivere Windows Defender Antivirus, skal du se [dette fejlfindingsemne](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    d. [Onboard to Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Kør simulering

1. Fra en ekstern mailkonto skal du sende en mail til den postkasse, der blev identificeret i trin 2 i afsnittet om krav til jagtmiljø. Medtag en vedhæftet fil, der tillades via eventuelle eksisterende politikker for mailfiltrering. Denne fil behøver ikke at være skadelig eller eksekverbar. Foreslåede filtyper <i> er.pdf, </i><i>.exe</i> (hvis det er tilladt) eller en Office som f.eks. en Word-fil.

2. Åbn den sendte mail fra den enhed, der er konfigureret som defineret i trin 3 i sektionen med krav til jagtmiljø. Åbn enten den vedhæftede fil, eller gem filen på enheden.

#### <a name="go-hunting"></a>Gå på jagt

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.

2. I navigationsruden skal du vælge **> Avanceret på jagt**.

3. Opret en forespørgsel, der starter, ved at indsamle mailbegivenheder.

   1. Vælg **Forespørgsel > Ny**.

   1. I **Mailgrupper** under **Avanceret jagt** skal du dobbeltklikke **på EmailEvents**. Det burde du kunne se i forespørgselsvinduet.

      ```console
      EmailEvents
      ```

   1. Rediger tidsrammen for forespørgslen til de sidste 24 timer. Hvis den mail, du sendte, da du kørte simulering ovenfor, var inden for de seneste 24 timer, kan du ellers ændre tidsrammen efter behov.

   1. Vælg **Kør forespørgsel**. Du kan have forskellige resultater afhængigt af dit pilotmiljø.

      > [!NOTE]
      > Se næste trin for at få filtreringsindstillinger til at begrænse dataretur.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-1.png" alt-text="Siden Avanceret jagt i Microsoft 365 Defender portal" lightbox="../../media/advanced-hunting-incident-response-try-1.png":::

        > [!NOTE]
        > Avanceret forespørgsel viser forespørgselsresultater som tabeldata. Du kan også vælge at få vist dataene i andre formattyper, f.eks. diagrammer.

   1. Kig på resultaterne, og se, om du kan identificere den mail, du har åbnet. Det kan tage op til to timer, før meddelelsen vises i avanceret jagt. For at indskrænke resultaterne kan du tilføje where-betingelsen til din forespørgsel til kun at søge efter mails, der har "yahoo.com" som deres AfsenderMailFromDomain. Her er et eksempel.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Klik på de resulterende rækker fra forespørgslen, så du kan undersøge posten.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-2.png" alt-text="Sektionen Undersøg post på siden Avanceret ræve Microsoft 365 Defender portalen" lightbox="../../media/advanced-hunting-incident-response-try-2.png":::

4. Nu hvor du har bekræftet, at du kan se mailen, kan du tilføje et filter for de vedhæftede filer. Fokuser på alle mails med vedhæftede filer i miljøet. Til denne simulering skal du fokusere på indgående mails, ikke dem, der sendes ud fra dit miljø. Fjern eventuelle filtre, du har tilføjet, for at finde din meddelelse og tilføje "| where **AttachmentCount > 0** and **EmailDirection** == **"Inbound""**

   Følgende forespørgsel viser dig resultatet med en kortere liste end din indledende forespørgsel for alle mailhændelser:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Medtag derefter oplysningerne om den vedhæftede fil (f.eks.: filnavn, hashes) til resultatsættet. Det gør du ved at deltage **i tabellen EmailAttachmentInfo** . De almindelige felter, der skal bruges til at deltage i, er i dette tilfælde **NetworkMessageId** **og RecipientObjectId**.

   Følgende forespørgsel indeholder også en ekstra linje "| **omdøb projekt EmailTimestamp=Timestamp**", som hjælper med at identificere, hvilket tidsstempel der var relateret til mailen kontra tidsstempler, der er relateret til filhandlinger, som du vil tilføje i næste trin.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Derefter skal du bruge **værdien SHA256** fra tabellen **EmailAttachmentInfo** til at finde **DeviceFileEvents** (filhandlinger, der skete på slutpunktet) for den pågældende hash hash. Det almindelige felt her er SHA256-hash'en for den vedhæftede fil.

   Den resulterende tabel indeholder nu oplysninger fra slutpunktet (Microsoft Defender til slutpunkt), f.eks. enhedsnavn, hvilken handling der blev udført (i dette tilfælde filtreret til kun at medtage FileCreated-hændelser), og hvor filen blev gemt. Det kontonavn, der er knyttet til processen, medtages også.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Du har nu oprettet en forespørgsel, der identificerer alle indgående mails, hvor brugeren har åbnet eller gemt den vedhæftede fil. Du kan også finjustere denne forespørgsel for at filtrere efter bestemte afsenderdomæner, filstørrelser, filtyper osv.

7. Funktioner er en særlig type joinforbindelse, som giver dig mulighed for at trække flere TI-data om en fil som dens oplysninger om dens underskriver og udsteder osv. For at få flere oplysninger om filen skal du bruge **funktionen FileProfile()** berigende:

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Oprette en registrering

Når du har oprettet en forespørgsel, der identificerer oplysninger, du gerne vil have besked  om, hvis de forekommer i fremtiden, kan du oprette en brugerdefineret registrering ud fra forespørgslen.

Brugerdefinerede registreringer kører forespørgslen i overensstemmelse med den frekvens, du har angivet, og resultaterne af forespørgslerne opretter sikkerhedsadvarsler baseret på de påsvarede aktiver, du vælger. Disse beskeder korreleres med hændelser og kan omdeles som andre sikkerhedsadvarsler, der genereres af et af produkterne.

1. På forespørgselssiden skal du fjerne linje 7 og 8, der blev tilføjet i trin 7 i gå på jagtinstruktioner, og klikke **på Opret registreringsregel**.

   :::image type="content" source="../../media/advanced-hunting-incident-response-try-3.png" alt-text="Afsnittet til redigering af forespørgsel på siden Avanceret ræve Microsoft 365 Defender portalen" lightbox="../../media/advanced-hunting-incident-response-try-3.png":::

   > [!NOTE]
   > Hvis du klikker **på Opret registreringsregel** , og du har syntaksfejl i forespørgslen, gemmes din registreringsregel ikke. Dobbelttjek din forespørgsel for at sikre, at der ikke er nogen fejl.

2. Udfyld de påkrævede felter med de oplysninger, der gør det muligt for sikkerhedsteamet at forstå beskeden, hvorfor den blev oprettet, og hvilke handlinger du forventer, de skal udføre.

   :::image type="content" source="../../media/mtp/fig23.png" alt-text="Siden med beskedoplysninger i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig23.png":::

   Sørg for, at du udfylder felterne med klarhed for at give den næste bruger en informeret beslutning om denne besked om registreringsregel

3. Vælg, hvilke enheder der påvirkes af denne besked. I dette tilfælde skal du vælge **Enhed** og **postkasse**.

   :::image type="content" source="../../media/mtp/fig24.png" alt-text="Detaljesiden for de på påvirkede enheder i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig24.png":::

4. Afgør, hvilke handlinger der skal foregå, hvis beskeden udløses. I dette tilfælde skal du køre en antivirusscanning, selvom der kan blive foretaget andre handlinger.

   :::image type="content" source="../../media/mtp/fig25.png" alt-text="Siden Handlinger i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig25.png":::

5. Vælg området for beskedreglen. Da denne forespørgsel involverer enheder, er enhedsgrupperne relevante i denne brugerdefinerede registrering i henhold til Microsoft Defender til slutpunktskontekst. Når du opretter en brugerdefineret registrering, der ikke omfatter enheder som på påvirkede enheder, gælder omfang ikke.

   :::image type="content" source="../../media/mtp/fig26.png" alt-text="Siden Omfang i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig26.png":::


   For dette pilotprojekt kan det være en god ide at begrænse denne regel til et undersæt af testenheder i produktionsmiljøet.

6. Vælg **Opret**. Vælg derefter **Brugerdefinerede registreringsregler** fra navigationspanelet.

   :::image type="content" source="../../media/mtp/fig27a.png" alt-text="Indstillingen Regler for brugerdefinerede registreringsregler i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig27a.png":::

   :::image type="content" source="../../media/mtp/fig27b.png" alt-text="Siden, der viser registreringsregler og eksekveringsoplysninger i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig27b.png":::

   Fra denne side kan du vælge registreringsreglen, som åbner en detaljeside.

   :::image type="content" source="../../media/mtp/fig28.png" alt-text="Den side, der viser detaljer om de udløste beskeder i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig28.png":::


### <a name="expert-training-on-advanced-hunting"></a>Ekspertkursus om avanceret jagt

**Sporing af adversæren** er en webcast-serie for nye sikkerhedsanalytikere og errerede trusselsskyggere. Den fører dig gennem det grundlæggende om avanceret er at lede hele vejen til at oprette dine egne avancerede forespørgsler. 

Se [Få ekspertkurser i avanceret jagt for](advanced-hunting-expert-training.md) at komme i gang.

### <a name="navigation-you-may-need"></a>Navigation, du skal muligvis bruge

[Oprette Microsoft 365 Defender Evalueringsmiljø](eval-create-eval-environment.md)
