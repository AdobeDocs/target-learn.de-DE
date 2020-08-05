---
title: Übersicht über die Adobe Target API
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations verfügt über eine dedizierte Reihe von APIs, mit denen Sie Ihren Katalog mit empfohlbaren Produkten und/oder Inhalten verwalten können. Ihre Empfehlungsalgorithmen und -Kampagnen zu verwalten; und geben Empfehlungen in JSON-, HTML- oder XML-Objekten für die Anzeige in Web-, Mobil-, E-Mail-, IOT- und anderen Kanälen ab.
kt: null
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Adobe Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: b66dbae616c9559f5d1b7bbedf2d9b383840973b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 2%

---


# Übersicht über die Adobe Target API

Adobe Target-APIs können nach Typ gruppiert werden.

| API-Typ | Was es Ihnen ermöglicht | Download-Link |
| --- | --- | --- |
| Admin | Erstellen, ändern und löschen Sie Aktivitäten, Audiencen, Angebote und andere Objekte (einschließlich [!DNL Recommendations] Entitäten, Kriterien, Entwürfe usw.). Die [!DNL Recommendations] APIs sind eine Art Admin-API.) | <UL><li>[Zielgruppe Admin API Postman Collection](https://developers.adobetarget.com/api/#admin-postman-collection)</li><li>[Recommendations API Postman Collection](https://developers.adobetarget.com/api/recommendations/#section/Postman)</li></ul> |
| Bereitstellung | Abrufen optimierter und personalisierter Inhalte vom [!DNL Target] für den Versand bis zum Endbenutzer. | [Zielgruppe Versand API Postman Collection](https://developers.adobetarget.com/api/delivery-api/#section/Getting-Started/Postman-Collection) |
| Berichterstellung | Exportieren Sie Aktivitäten und andere Berichte. | Berichte-APIs sind in der [Zielgruppe Admin API Postman-Sammlung](https://developers.adobetarget.com/api/#admin-postman-collection)enthalten. |
| Profil | Abrufen und Ändern von in Adobe Target gespeicherten Profilen. | [Zielgruppe Profil API Postman Collection](https://developers.adobetarget.com/api/#profiles) |

Beachten Sie die Unterscheidung zwischen **Admin-APIs** (einschließlich der [!DNL Recommendations] APIs), mit denen Sie verschiedene Aspekte von Adobe Target konfigurieren können, und **Versand-APIs**, mit denen Sie Inhalte abrufen können. Admin-APIs erfordern eine Authentifizierung, Versand-APIs dagegen nicht.

Um Adobe Target Admin-APIs zu verwenden, müssen Sie zunächst die Authentifizierung mit der Adobe I/O konfigurieren.

[Nächste &quot;Authentifizierung konfigurieren&quot;>](configure-io-target-integration.md)
