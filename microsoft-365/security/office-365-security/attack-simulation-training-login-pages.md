---
title: Logonsider i kursus i angrebssimulering
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan få mere at vide om, hvordan de opretter og administrerer logonsider for simulerede phishingangreb i Microsoft Defender for Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: 5ecbdddfff4d528c1af8e20cf4d3831d3250eacc
ms.sourcegitcommit: 03543c27c33427ac7f11af4c04fff35a181a2524
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66609285"
---
# <a name="login-pages-in-attack-simulation-training"></a>Logonsider i kursus i angrebssimulering

**Gælder for** [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)

I oplæring i simulering af angreb i Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 vises logonsider for brugere i simuleringer, der bruger **Credential Harvest** og Link i [teknikker til social engineering af](attack-simulation-training.md#select-a-social-engineering-technique) **vedhæftede filer**.

Hvis du vil se de tilgængelige logonsider, skal du åbne portalen Microsoft 365 Defender på <https://security.microsoft.com>, gå til **Mail & samarbejde** \> Oplæring **af simulering af angreb** \> **Bibliotek med simulering af indhold** \> og derefter vælge **Logonsider**. Hvis du vil gå direkte til fanen **Simuleringsindholdsbibliotek** , hvor du kan vælge **Logonsider**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Logonsider** har to faner:

- **Globale logonsider**: Indeholder de indbyggede logonsider, der ikke kan ændres. Der er fire indbyggede logonsider oversat til mere end 12 sprog:
  - **GitHub-logonside**
  - **LinkedIn-logonside**
  - **Microsoft-logonside**
  - **Logonside, der ikke er mærket**

- **Lejerlogonsider**: Indeholder de brugerdefinerede logonsider, du har oprettet.

Følgende oplysninger vises for hver logonside:

- **Navn**
- **Sprog**
- **Kilde**: For indbyggede logonsider er værdien **Global**. For brugerdefinerede logonsider er værdien **Lejer**.
- **Status**: **Klar** eller **Kladde**.
- **Oprettet af**: For indbyggede logonsider er værdien **Microsoft**. For brugerdefinerede logonsider er værdien UPN for den bruger, der oprettede logonsiden.
- **Senest ændret**

Hvis du vil finde en logonside på listen, skal du bruge søgeikonet ![.](../../media/m365-cc-sc-search-icon.png) **Søgefelt** for at finde navnet på logonsiden.

Klik på ![Filterikon.](../../media/m365-cc-sc-filter-icon.png) **Filtrer** for at filtrere logonsiderne efter **sprog** eller **status**.

Hvis du vil fjerne en eller flere kolonner, der vises, skal du klikke på ![ikonet Tilpas kolonner.](../../media/m365-cc-sc-customize-icon.png) **Tilpas kolonner**.

Når du vælger en logonside på listen, vises der et pop op-vindue med oplysninger med følgende oplysninger:

- ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Redigering** er kun tilgængelig på brugerdefinerede logonsider på fanen **Lejerlogonsider** .
- ![Markér som standardikon.](../../media/m365-cc-sc-set-as-default-icon.png) **Markér som standard** for at gøre denne logonside til standardvalget i **Høst af legitimationsoplysninger** eller Link i [nyttedata](attack-simulation-training-payloads.md) til **vedhæftede filer** eller [automatiseringer af nyttedata](attack-simulation-training-payload-automations.md). Hvis logonsiden allerede er standard, ![skal du markere som standardikon.](../../media/m365-cc-sc-set-as-default-icon.png) **Markér som standard** er ikke tilgængelig.
- **Fanen Eksempel** : Få vist logonsiden, som brugerne kan se den. **Side 1** - og **side 2-links** er tilgængelige nederst på siden for tosidede logonsider.
- Fanen **Detaljer**: Få vist oplysninger om logonsiden:
  - **Beskrivelse**
  - **Status**: **Klar** eller **Kladde**.
  - **Kilde til logonside**: For indbyggede logonsider er værdien **Global**. For brugerdefinerede logonsider er værdien **Lejer**.
  - **Ændret af**
  - **Sprog**
  - **Senest ændret**

## <a name="create-login-pages"></a>Opret logonsider

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til Fanen \> **Mail & oplæring af simulering** af **angrebssimuleringsindholdsbibliotek**  \> \> og derefter vælge **Logonsider**. Hvis du vil gå direkte til fanen **Simuleringsindholdsbibliotek** , hvor du kan vælge **Logonsider**, skal du bruge <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.
Du kan oprette brugerdefinerede logonsider på følgende placeringer:

   Klik på ![Opret nyt ikon.](../../media/m365-cc-sc-create-icon.png) **Opret ny** for at starte guiden Opret slutbrugerlogonside.

   > [!NOTE]
   > Ikonet ![Opret ny.](../../media/m365-cc-sc-create-icon.png) **Opret ny** er også tilgængelig under trinnet til valg af nyttedata til oprettelse af en simulering. Du kan få flere oplysninger under [Simuler et phishing-angreb med oplæring i simulering af angreb i Defender for Office 365](attack-simulation-training.md).
   >
   > Når som helst under oprettelsesguiden kan du klikke på **Gem og luk** for at gemme dine fremskridt og fortsætte med at konfigurere logonsiden senere. Du kan fortsætte, hvor du slap, ved at vælge logonsiden under fanen **Lejerlogonsider** på **logonsider** og derefter klikke på ![ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**. Den delvist fuldførte logonside **har statusværdien** **Kladde**.

2. Konfigurer følgende indstillinger på siden **Definer oplysninger om logon** :
   - **Navn**: Angiv et entydigt navn.
   - **Beskrivelse**: Angiv en valgfri beskrivelse.

   Klik på **Næste**, når du er færdig.

3. Konfigurer følgende indstillinger på **siden Konfigurer logon** :

   - **Vælg et sprog**: De tilgængelige værdier er: **kinesisk (forenklet),** **kinesisk (traditionelt),** **engelsk**, **fransk**, **tysk**, **italiensk**, **japansk**, **koreansk**, **portugisisk**, **russisk**, **spansk** og **hollandsk**.

   - **Gør dette til standardlogonsiden**: Hvis du vælger denne indstilling, vil logonsiden være standardvalget i **Høst af legitimationsoplysninger** eller Link i [nyttedata](attack-simulation-training-payloads.md) til **vedhæftede filer** eller [automatiseringer af nyttedata](attack-simulation-training-payload-automations.md).

   - **Opret et tosidet logon**: Hvis du ikke vælger denne indstilling, er logonsiden én side. Hvis du vælger denne indstilling, vises fanerne **Side 1** og **Side 2** , som du kan konfigurere separat.

     - Under fanen **Tekst** er der en RTF-editor tilgængelig, så du kan oprette din logonside.

       - Brug kontrolelementet **Dynamic tag** til at tilpasse logonsiden ved at indsætte de tilgængelige mærker:
         - **Indsæt brugernavn**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${userName}`.
         - **Indsæt mail**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${emailAddress}`.
         - **Indsæt dato**: Den værdi, der tilføjes i meddelelsens brødtekst, er `${date|MM/dd/yyyy|offset}`.

       - Brug kontrolelementet **Brug fra standard** til at vælge en indbygget logonside, der skal starte med som en skabelon.

       - Knapkontrolelementet **Tilføj næste** er kun tilgængeligt på **side 1** med tosidet logon. Standardteksten på knappen er **Næste** , men du kan ændre den.

       - Kontrolelementet **Tilføj kompromisknap** i er tilgængeligt ved logon på én side eller på **side 2** med tosidet logon. Standardteksten på knappen er **Send**, men du kan ændre den.

     - Under fanen **Kode** kan du få vist og redigere HTML-koden direkte. Formatering og andre kontrolelementer som **Dynamic tag** og **Use from default** eller **Add compromise button** er ikke tilgængelige.

   - Brug knappen **Vis logonside** øverst på siden til at gennemse logonsiden.

   Klik på **Næste**, når du er færdig.

4. På **siden Gennemse logon** kan du gennemse oplysningerne om din logonside.

   Du kan vælge **Rediger** i hver sektion for at redigere indstillingerne i sektionen. Du kan også klikke på **Tilbage** eller vælge den specifikke side i guiden.

   Klik på **Send**, når du er færdig.

5. På siden **Ny logonside \<Name\> , der er oprettet** , kan du bruge linkene til at oprette en ny logonside, starte en simulering eller få vist alle logonsider.

   Klik på **Udført**, når du er færdig.

Tilbage på fanen **Lejerlogonsider** på **logonsider** er den logonside, du har oprettet, nu på listen.

## <a name="modify-login-pages"></a>Rediger logonsider

Du kan ikke ændre indbyggede logonsider under fanen **Globale logonsider** . Du kan kun redigere brugerdefinerede logonsider under fanen **Lejerlogonsider** .

Hvis du vil redigere en eksisterende brugerdefineret logonside under fanen **Lejerlogonsider** , skal du gøre et af følgende:

- Vælg logonsiden på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet ![Rediger.](../../media/m365-cc-sc-edit-icon.png) **Redigeringsikon** , der vises.
- Klik **på ⋮** (**handlinger**) mellem logonsidens **navn** og **sprogværdier** på listen, og vælg ![derefter ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
- Vælg logonsiden på listen ved at klikke på navnet. Klik på ![Ikonet Rediger i det pop op-vindue med detaljer, der åbnes.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.

Guiden logonside åbnes med indstillingerne og værdierne for den valgte logonside. Trinnene er de samme som beskrevet i afsnittet [Opret logonsider](#create-login-pages) .

## <a name="copy-login-pages"></a>Kopiér logonsider

Hvis du vil kopiere en eksisterende logonside på **fanerne Lejerlogon** eller **Globale logonsider** , skal du gøre et af følgende:

- Vælg logonsiden på listen ved at klikke på afkrydsningsfeltet, og klik derefter på ikonet ![Opret en kopi.](../../media/m365-cc-sc-edit-icon.png) **Opret et kopiikon** , der vises.
- Klik på **⋮** (**handlinger**) mellem værdierne **Navn** og **Sprog** på logonsiden på listen, og vælg ![derefter Opret et kopiikon.](../../media/m365-cc-sc-edit-icon.png) **Opret en kopi**.

Guiden logonside åbnes med indstillingerne og værdierne for den valgte logonside. Trinnene er de samme som beskrevet i afsnittet [Opret logonsider](#create-login-pages) .

> [!NOTE]
> Når du kopierer en indbygget logonside under fanen **Globale logonsider** , skal du sørge for at ændre værdien **Navn** . Dette trin sikrer, at kopien gemmes som en brugerdefineret logonside på fanen **Lejerlogonsider** .
>
> Kontrolelementet **Brug fra standard** på siden **Konfigurer logonside** i guiden Logonside giver dig mulighed for at kopiere indholdet af en indbygget logonside.

## <a name="remove-login-pages"></a>Fjern logonsider

Du kan ikke fjerne indbyggede logonsider fra fanen **Globale logonsider** . Du kan kun fjerne brugerdefinerede logonsider under fanen **Lejerlogonsider** .

Benyt en af følgende fremgangsmåder for at fjerne en eksisterende brugerdefineret logonside fra fanen **Lejerlogonsider** :

- Vælg logonsiden på listen ved at klikke på afkrydsningsfeltet, og klik derefter på ikonet ![Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet** ikon, der vises.
- Klik **på ⋮** (**handlinger**) mellem værdierne **Navn** og **Sprog** på logonsiden på listen, og vælg ![derefter Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

## <a name="make-a-login-page-the-default"></a>Gør en logonside til standardsiden

Standardlogonsiden er det standardvalg, der bruges i **Høst af legitimationsoplysninger** eller Link i [nyttedata](attack-simulation-training-payloads.md) til **vedhæftede filer** eller [automatiseringer af nyttedata](attack-simulation-training-payload-automations.md).

Hvis du vil gøre en logonside til standard på fanerne **Lejerlogonsider** eller **Globale logonsider** , skal du gøre et af følgende:

- Vælg logonsiden på listen ved at klikke på afkrydsningsfeltet. Klik på ikonet Markér ![som standard.](../../media/m365-cc-sc-set-as-default-icon.png) **Markér som standardikon** , der vises.
- Klik **på ⋮** (**handlinger**) mellem værdierne **Navn** og **Sprog** på logonsiden på listen, og vælg ![derefter Markér som standardikon.](../../media/m365-cc-sc-set-as-default-icon.png) **Markér som standard**.
- Vælg logonsiden på listen ved at klikke på navnet. Klik på ![Markér som standardikon i det pop op-vindue med detaljer, der åbnes.](../../media/m365-cc-sc-set-as-default-icon.png) **Markér som standard**.
- Vælg **Gør dette til standardlogonsiden** på siden **Konfigurer logonside** i guiden, når du [opretter eller ændrer en logonside](#create-login-pages).

> [!NOTE]
> De tidligere procedurer er ikke tilgængelige, hvis logonsiden allerede er standard.
>
> Standardlogonsiden er også markeret på listen, selvom du muligvis skal udvide kolonnen **Name** for at se den:
>
> ![Den standardlogonside, der er markeret på listen over logonsider i oplæringen til simulering af angreb.](../../media/attack-sim-training-login-pages-default.png)

## <a name="related-links"></a>Relaterede links

[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)

[Opret en simulering af phishingangreb](attack-simulation-training.md)

[Simuleringsautomatiseringer til oplæring af simulering af angreb](attack-simulation-training-simulation-automations.md)
