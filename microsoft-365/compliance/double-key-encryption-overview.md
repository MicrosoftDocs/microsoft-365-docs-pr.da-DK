---
title: Oversigt over kryptering af dobbeltnøgle og ofte stillede spørgsmål
description: Ofte stillede spørgsmål om kryptering med dobbelt nøgle.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: c42104ccb74aba71b143d1ee31b0ed5893d9396f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641828"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Ofte stillede spørgsmål om kryptering med dobbelt nøgle

Har du et spørgsmål om, hvordan dobbeltnøglekryptering fungerer? Se efter et svar her.

## <a name="what-is-double-key-encryption-dke"></a>Hvad er dobbeltnøglekryptering (DKE)?

Dobbeltnøglekryptering gør det muligt for kunder at beskytte deres meget følsomme data, så de opfylder specialiserede krav. Det hjælper dig med at bevare fuld kontrol over deres krypteringsnøgler. Den bruger to nøgler til at beskytte data. én nøgle i dit kontrolelement og en anden nøgle, der er gemt sikkert i Microsoft Azure. Visning af data, der er beskyttet med dobbelt nøglekryptering, kræver adgang til begge nøgler. Da Microsoft kun kan få adgang til én af disse nøgler, er beskyttede data stadig utilgængelige for Microsoft, så det sikres, at du har fuld kontrol over beskyttelse af personlige oplysninger og sikkerhed.  

Du kan hoste den dobbeltnøglekrypteringstjeneste, der bruges til at anmode om din nøgle, på en placering efter eget valg (server til administration af nøgler i det lokale miljø eller i cloudmiljøet). Du vedligeholder tjenesten på samme måde som alle andre programmer. Med dobbeltnøglekryptering kan du styre adgangen til tjenesten Dobbeltnøglekryptering. Du kan gemme dine meget følsomme data i det lokale miljø eller flytte dem til cloudmiljøet. Du kan være sikker på at forhindre tredjepartsadgang, fordi du bevarer fuld kontrol over din nøgle. Dobbeltnøglekryptering giver dig mulighed for at gemme dine data og din nøgle på samme placering.

DKE hjælper dig med at opfylde lovmæssige krav på tværs af flere regler og standarder, f.eks. PERSONDATA (General Data Protection Regulation), HEALTH Insurance Portability and Accountability Act (HIPAA), Gramm-Leach-Bliley Act (GLBA), Ruslands lov om lokalisering af data – Federal Law No. 242-FZ, Australia's Federal Privacy Act 1988, og New Zealand's Privacy Act 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Kan jeg bruge kryptering med dobbelt nøgle med indbygget følsomhedsmærkning i Microsoft Office?

Du skal bruge Azure Information Protection Unified-mærkatklienten til at beskytte dokumenter med kryptering med dobbelt nøgle. I øjeblikket kan du ikke bruge den indbyggede følsomhedsmærkatering i Microsoft Office.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Hvilke Microsoft 365 Apps kan jeg bruge sammen med DKE?

Du kan bruge DKE-mærkater til at beskytte dokumenter ved hjælp af skrivebordsversionerne af Word, Excel og PowerPoint på Windows. Sørg for, at du bruger *.12711 eller nyere (desktopversioner af Word, PowerPoint og Excel) på Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Hvordan adskiller dobbelt nøglekryptering sig fra den eksisterende HYOK-løsning (Hold Your Own Key)?

Kryptering med dobbelt nøgle krypterer dine data med to nøgler. Din krypteringsnøgle er i din kontrol, og den anden nøgle gemmes i Microsoft Azure, så du kan flytte dine krypterede data til cloudmiljøet. HYOK beskytter dit indhold med kun én nøgle, og nøglen er altid i det lokale miljø.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Kan krypterede dokumenter med dobbelt nøgle deles eksternt?

Du kan dele krypterede dokumenter med dobbelt nøgle med brugere på en separat lejer, så længe disse brugere:

- Du skal have den nødvendige tilladelse til at få adgang til din nøgle i din dobbeltnøglekrypteringstjeneste.

- Du skal have den nødvendige tilladelse til at få adgang til din nøgle i Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Hvad sker der med dokumenter, der er beskyttet med HYOK?

Installation af kryptering med dobbelt nøgle påvirker ikke den eksisterende HYOK-konfiguration. Vi anbefaler dog, at du begynder at bruge dobbeltnøglekryptering parallelt med HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Kan jeg køre kryptering med dobbelt nøgle i mit luftgabede miljø, der ikke er fra Microsoft?

DKE understøtter ikke disse miljøer, fordi tjenesten kræver adgang til Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Hvor kan jeg gemme krypterede dokumenter med dobbelt nøgle?

Du kan gemme krypterede dokumenter med dobbelt nøgle i det lokale miljø eller i cloudmiljøet. I skyen kan du flytte krypteret indhold til SharePoint Online og OneDrive for Business. Da Microsoft ikke har adgang til din private nøgle, forbliver de krypterede data uigennemsigtige for Microsoft. Det betyder også, at du ikke kan få vist de krypterede dokumenter online i Office Web Apps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Hvilke områder og sprog er dobbeltnøglekryptering tilgængelig i? Er kryptering med dobbelt nøgle tilgængelig over hele verden?

DKE-mærkater lokaliseres til de samme sprog som andre følsomhedsmærkater i Microsoft Purview Information Protection. Dobbeltnøglekryptering er tilgængelig over hele verden.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Kan jeg konvertere et ikke-DKE-mærkat til et DKE-mærkat?

Nej. Du kan ikke føje DKE til en mærkat, når du har oprettet den. Du skal i stedet vælge **Brug dobbeltnøglekryptering** og angive URL-adressen til din dobbeltnøglekrypteringstjeneste, når du opretter mærkaten.

## <a name="how-do-i-roll-my-dke-keys"></a>Hvordan gør jeg rulle mine DKE-nøgler?

Du kan finde instruktioner i at rulle (også kaldet roterende eller omtaste) den nøgle, du gemmer i Azure, under [Handlinger for din Azure Information Protection-lejernøgle](/azure/information-protection/operations-customer-managed-tenant-key).

Se [Lejer- og nøgleindstillinger](double-key-encryption.md#tenant-and-key-settings) for at få oplysninger om, hvordan du opretter en ny nøgle til DKE-tjenesten.

Når du opretter en nøgle, konfigurerer du et navn og et GUID. Hvis du derefter roterer en nøgle, beholder du den gamle post med navnet og GUID, men tilføjer en ny post med samme navn, men med et andet GUID. Den nye nøgle angives som aktiv, så API'en for den offentlige nøgle begynder at returnere den til ny kryptering. Begge nøgler er tilgængelige til dekryptering, så nyt indhold og gammelt indhold kan dekrypteres.
