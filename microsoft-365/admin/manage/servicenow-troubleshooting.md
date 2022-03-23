---
title: Fejlfinding Microsoft 365 supportintegration med ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Omfangsstyret certificeret programinstallation og konfigurationsvejledning for ServiceNow.
ms.openlocfilehash: bac3981b728ac997839e7ac99a9411a8da244add
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593605"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Fejlfinding Microsoft 365 supportintegration med ServiceNow

| \#  | Problem  | Diagnosticeringshandling     |
|-----|--------------------------------|----------------------|
| 1   | Kan ikke se Microsoft 365 **support**                                                                                                                                                                                    | Bekræfte den aktuelle visning og **Alle systemlogfiler** &gt; **med** filteret xmiomsm365assit\_\_\_                        |
| 2   | Vælg **anbefalede Microsoft-løsninger** , men få fejlen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre konfigurationstrinnene for appen."                                                                      | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 3   | Vælg **anbefalede Microsoft-løsninger** , men får fejlen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre det endelige opsætningstrin for appen."                                                                | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 4   | Skriv problemet i søgefeltet, og vælg **anbefalede Microsoft-løsninger** , men få fejlmeddelelsen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre konfigurationstrinnene for appen."                                   | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 5   | Skriv problem i søgefeltet, og vælg **anbefalede Microsoft-løsninger** , men få fejlmeddelelsen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre det endelige trin til opsætning af appen."                                 | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 6   | Vælg **Kontakt Microsoft support**, men få fejlmeddelelsen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre konfigurationstrinnene for appen."                                                                       | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 7   | Vælg **Kontakt Microsoft support**, men få fejlen "Kontakt din ServiceNow-administrator, og bed vedkommende om at fuldføre det endelige trin til opsætning af appen."                                                                 | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 8   | Vælg **Kontakt Microsoft support**, men få fejlen "{EmailAddress} er ikke en gyldig Microsoft 365 administratorkonto. Du skal Microsoft 365 administratorrettigheder for at åbne en serviceanmodning. Sammenkæd administratorkontoen i appen." | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 9   | Vælg **anbefalede Microsoft-løsninger,** men der vises ikke noget                                                                                                                                                            | Kontrollere **systemlogfiler – udgående HTTP-logfiler** med login.microsoftonline.com og connector.rave.microsoft.com |
| 10  | Vælg **anbefalede Microsoft-løsninger,** men få fejlen "Kontakt app-support."                                                                                                                                     | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 11  | Skriv problem i søgefeltet, og vælg **anbefalede Microsoft-løsninger,** men der vises ikke noget                                                                                                                             | Kontrollere **systemlogfiler – udgående HTTP-logfiler** med login.microsoftonline.com og connector.rave.microsoft.com |
| 12  | Skriv problem i søgefeltet, og vælg **anbefalede Microsoft-løsninger,** men få fejlen "Kontakt app-support."                                                                                                      | Kontrollér fejlmeddelelsen oven på formularen og **Systemlogfiler** &gt; alle med filter xmiomsm365assit \_\_\_     |
| 13  | Brugeren vælger Kontakt **Microsoft-support**, men der sker ikke noget                                                                                                                                                            | Kontrollere **systemlogfiler – udgående HTTP-logfiler** med login.microsoftonline.com og connector.rave.microsoft.com |
| 14  | Kan ikke se den anbefalede Microsoft-løsning efter at have genåbnet hændelsen                                                                                                                                                      | Kontrollér **alle systemlogfiler** &gt; **med** filter xmiomsm365assit\_\_\_                                              |
| 15  | Kan ikke se Microsoft-sager ved genåbning af hændelsen, der blev overført til Microsoft support                                                                                                                            | Kontrollér **alle systemlogfiler** &gt; **med** filter xmiomsm365assit\_\_\_                                              |
| 16  | Kan ikke gemme oplysninger om billet, får fejlen "Kan ikke gemme oplysninger om billet. Kontakt App-support."                                                                                                                          | Kontrollér fejlmeddelelsen oven på formularen                                                                            |
