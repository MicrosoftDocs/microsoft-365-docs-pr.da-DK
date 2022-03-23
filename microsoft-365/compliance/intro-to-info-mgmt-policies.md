---
title: Introduktion til politikker for administration af oplysninger
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 5/16/2014
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- WSU150
- SPO160
- OSU150
- MET150
ms.assetid: 63a0b501-ba59-44b7-a35c-999f3be057b2
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du bruger politikker for administration af oplysninger til at styre og registrere ting som, hvor lang tid indhold opbevares, eller hvad brugerne kan bruge indholdet til.
ms.openlocfilehash: 98eae2a08aa246a1f0ebe7d037103a82c132d060
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587906"
---
# <a name="introduction-to-information-management-policies"></a>Introduktion til politikker for administration af oplysninger

En politik for administration af oplysninger er et sæt regler for en type indhold. Politikker for administration af oplysninger giver organisationer mulighed for at styre og registrere ting som, hvor lang tid indhold bevares, eller hvad brugerne kan bruge indholdet til. Politikker for administration af oplysninger kan hjælpe organisationer med at overholde juridiske eller statslige love og forordninger, eller de kan blot håndhæve interne forretningsprocesser. 
  
En organisation, der skal overholde statslige love og forordninger, der kræver, at de har "tilstrækkelige kontroller" af deres regnskaber, kan f.eks. oprette en eller flere politikker for administration af oplysninger, der overvåge bestemte handlinger i oprettelses- og godkendelsesprocessen for alle dokumenter, der er relateret til finansielle arkiver.
  
Du kan finde oplysninger om, hvordan du gør, [under Oprette og anvende politikker for administration af oplysninger](create-info-mgmt-policies.md).
  
## <a name="features-of-information-management-policies"></a>Funktioner i politikker for administration af oplysninger
<a name="__top"> </a>

Der er fire grundlæggende kategorier af foruddefinerede politikfunktioner, som organisationer kan bruge enkeltvis eller i kombination til at administrere indhold og processer. 
  
![Typer af indholdspolitikker.](../media/19fcb8a3-974b-40d3-a13f-b76088d122f8.png)
  
Funktionen Overvågningspolitik hjælper organisationer med at analysere, hvordan deres systemer til indholdsstyring bruges ved at logføring af hændelser og handlinger, der udføres på dokumenter og listeelementer. Du kan konfigurere politikfunktionen Overvågning til at logføre hændelser, f.eks. når et dokument eller et element redigeres, vises, tjekkes ind, tjekkes ud, slettes eller får ændret tilladelserne. Alle overvågningsoplysningerne gemmes i en enkelt overvågningslog på serveren, og webstedsadministratorer kan køre rapporter på den. 
  
Politikken Udløb hjælper organisationer med at slette eller fjerne forældet indhold fra deres websteder på en ensartet og registrerbar måde. Dette hjælper dig med at administrere både de omkostninger og risici, der er forbundet med at bevare forældet indhold. Du kan konfigurere en politik for udløb for at angive, at visse typer indhold udløber på en bestemt dato eller inden for en periode, efter dokumentet blev oprettet eller senest blev ændret.
  
Organisationer kan også oprette og implementere brugerdefinerede politikfunktioner, der opfylder specifikke behov. En produktionsorganisation kan f.eks. definere en politik for administration af oplysninger for alle kladder med produktdesignspecifikationer, der forhindrer brugere i at udskrive kopier af disse dokumenter på usikre printere. Hvis du vil definere denne type politik for administration af oplysninger, kan du oprette og implementere en politikfunktion til begrænsning af udskrivning, som kan føjes til den relevante politik for administration af oplysninger for produktdesignspecifikationens indholdstype.
  
## <a name="locations-to-use-an-information-management-policy"></a>Placeringer, der bruges til at bruge en politik for administration af oplysninger
<a name="__toc340213528"> </a>

Hvis du vil implementere en politik for administration af oplysninger, skal du føje den til en liste, et bibliotek eller en indholdstype på et websted. Det sted, hvor du opretter eller tilføjer en politik for administration af oplysninger, påvirker, hvor bredt politikken gælder, eller hvor bredt den kan anvendes. Du kan:
  
 **Opret en politik for en gruppe af websteder, og føj derefter denne politik til en indholdstype, en liste eller et bibliotek** Du kan oprette en politik for en gruppe af websteder på listen Politikker på det øverste niveau i en gruppe af websteder. Når du har oprettet en politik for en gruppe af websteder, kan du eksportere den, så administratorer af andre grupper af websteder kan importere den til deres Politikker-liste. Når du opretter en politik for en gruppe af websteder, der kan eksporteres, kan du standardisere politikkerne for administration af oplysninger på tværs af webstederne i organisationen. 
  
Når du føjer en politik for en gruppe af websteder til en webstedsindholdstype, og en forekomst af den webstedsindholdstype føjes til en liste eller et bibliotek, kan ejeren af listen eller biblioteket ikke ændre politikken for gruppen af websteder for listen eller biblioteket. Tilføjelse af en politik for en gruppe af websteder til en webstedsindholdstype er en god måde at sikre, at politikkerne for gruppen af websteder overholdes på hvert niveau i webstedshierarkiet.
  
![Linket Politikskabelon til indholdstype på siden Indstillinger websted.](../media/26d3466a-23ec-443f-88f0-2aaff38e992b.png)
  
 **Opret en politik for administration af oplysninger for en webstedsindholdstype** i galleriet Webstedsindholdstype på det øverste niveau, og føj derefter indholdstypen til en eller flere lister eller biblioteker Du kan også oprette en politik for administration af oplysninger direkte for en webstedsindholdstype og derefter knytte en forekomst af webstedsindholdstypen til flere lister eller biblioteker. Hvis du opretter en politik for administration af oplysninger på denne måde, har alle elementer i gruppen af websteder med den pågældende indholdstype eller en indholdstype, der nedarver fra den pågældende indholdstype, politikken. Men hvis du opretter en politik for administration af oplysninger direkte for en webstedsindholdstype, er det sværere at genbruge denne politik for administration af oplysninger i andre grupper af websteder, fordi de politikker, der oprettes på denne måde, ikke kan eksporteres. 
  
![Link til webstedsindholdstyper på Indstillinger side.](../media/6f6fa51f-15d7-4782-b06f-a7b36e874cd3.png)
  
![Link til politik for administration af oplysninger på siden med indstillinger for en webstedsindholdstype.](../media/15d83a34-6c8f-4b6e-b6ee-e9b0a70cbb4b.png)
  
Bemærk! Hvis du vil styre, hvilke politikker der bruges i en gruppe af websteder, kan administratorer af grupper af websteder deaktivere muligheden for at angive politikfunktioner direkte på en indholdstype. Når denne begrænsning gælder, kan de brugere, der opretter indholdstyper, kun vælge politikker på listen Politikker for gruppe af websteder.
  
 **Opret en politik for administration af oplysninger for en liste eller et bibliotek** Hvis organisationen har brug for at anvende en bestemt politik for administration af oplysninger på et meget begrænset sæt indhold, kan du oprette en politik for administration af oplysninger, som kun gælder for en enkelt liste eller et enkelt bibliotek. Denne metode til at oprette en politik for administration af oplysninger er den mindst fleksible, fordi politikken kun gælder for ét sted, og den kan ikke eksporteres eller genbruges til andre placeringer. Nogle gange kan det dog være nødvendigt at oprette entydige politikker for administration af oplysninger med begrænset anvendelsesmuligheder for at håndtere bestemte situationer. 
  
![Link til politikker for administration af oplysninger på indstillingssiden for dokumentbibliotek.](../media/9fa6d366-6aab-49e1-a05c-898ac6f536e6.png)
  
Bemærkninger 
  
Du kan kun oprette en politik for administration af oplysninger for en liste eller et bibliotek, hvis listen eller biblioteket ikke understøtter flere indholdstyper. Hvis en liste eller et bibliotek understøtter flere indholdstyper, skal du definere en politik for administration af oplysninger for hver enkelt listeindholdstype, der er knyttet til listen eller biblioteket. (Forekomster af en webstedsindholdstype, der er knyttet til en bestemt liste eller et bestemt bibliotek, kaldes listeindholdstyper).
  
Hvis du vil styre, hvilke politikker der bruges i en gruppe af websteder, kan administratorer af grupper af websteder deaktivere muligheden for at angive politikfunktioner direkte på en liste eller i et bibliotek. Når denne begrænsning gælder, kan de brugere, der administrerer lister eller biblioteker, kun vælge politikker på listen Politikker for gruppe af websteder.
  
[En politik for administration af oplysninger er et sæt regler for en type indhold. Politikker for administration af oplysninger giver organisationer mulighed for at styre og registrere ting som, hvor lang tid indhold bevares, eller hvad brugerne kan bruge indholdet til. Politikker for administration af oplysninger kan hjælpe organisationer med at overholde juridiske eller statslige love og forordninger, eller de kan blot håndhæve interne forretningsprocesser. En organisation, der skal overholde statslige love og forordninger, der kræver, at de har "tilstrækkelige kontroller" af deres regnskaber, kan f.eks. oprette en eller flere politikker for administration af oplysninger, der overvåge bestemte handlinger i oprettelses- og godkendelsesprocessen for alle dokumenter, der er relateret til finansielle arkiver. Du kan finde oplysninger om, hvordan du gør, under Oprette og anvende politikker for administration af oplysninger.](intro-to-info-mgmt-policies.md#__top)
  

