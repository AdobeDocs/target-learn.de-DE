---
title: Übersicht über die Adobe Recommendations API
keywords: recommendations;adobe recommendations;premium;api;apis
description: Adobe Target Recommendations verfügt über eine dedizierte Reihe von APIs, mit denen Sie Ihren Katalog mit empfohlbaren Produkten und/oder Inhalten verwalten können. Ihre Empfehlungsalgorithmen und -Kampagnen zu verwalten; und geben Empfehlungen in JSON-, HTML- oder XML-Objekten für die Anzeige in Web-, Mobil-, E-Mail-, IOT- und anderen Kanälen ab.
kt: 3815
audience: developer
doc-type: tutorial
activity: use
feature: api
topics: recommendations;adobe recommendations;premium;api;apis
solution: Target
author: Judy Kim
translation-type: tm+mt
source-git-commit: c221f434ce9daec03dbb4d897343775b40b14462
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 1%

---


# Übersicht über die Adobe Recommendations API

Zu den für [!DNL Recommendations] relevanten APIs zählen [Admin-APIs](https://docs.adobe.com/content/help/en/target/using/apis/api-overview.html), mit denen Sie:

* Verwalten Sie Ihren Katalog von empfohlenen Produkten oder Inhalten
* Verwalten Sie Ihre [!DNL Recommendations]-Algorithmen und -Aktivitäten

Mit der [!DNL Target] [Versand-API](https://docs.adobe.com/content/help/en/target/using/apis/api-overview.html) für Recommendations können Sie auch:

* Rufen Sie Empfehlungen in JSON-, HTML- oder XML-Objekten ab, damit sie im Web, auf Mobilgeräten, in E-Mails, im Internet der Dinge (IOT) und anderen Kanälen angezeigt werden können.

## Übungsbeschreibung

Dieses Lernprogramm führt Entwickler durch praktische Verfahren, mit denen mithilfe der [!DNL Recommendations]-APIs [!DNL Recommendations]-Kataloge und benutzerspezifische Kriterien konfiguriert und verwaltet werden, sowie mit der Versand-API zum Abrufen von Empfehlungsinhalten. Am Ende dieses Lernprogramms können Sie:

* Entitäten mit der Recommendations API konfigurieren und verwalten
* Benutzerdefinierte Kriterien mithilfe der Recommendations API konfigurieren und verwalten
* Verstehen Sie, wie Sie Recommendations mit der Versand-API verwenden, um Empfehlungsergebnisse auf Nicht-HTML-Geräten zu verwenden.

## Zielgruppe

Dieses Lernprogramm richtet sich an Entwickler, die neue APIs für Zielgruppe oder Recommendations APIs verwenden.

## Voraussetzungen

Für die Verwendung der Admin-APIs der Zielgruppe ist [Adobe-Authentifizierungs-Setup](../apis/configure-io-target-integration.md) erforderlich. Vergewissern Sie sich, dass Sie diese Konfiguration vorgenommen haben, bevor Sie dieses Lernprogramm beginnen.

## Ressourcen

Beachten Sie die folgenden Ressourcen, die erforderlich sind, um dieses Lernprogramm zu verstehen und es erfolgreich zu befolgen:

| Ressource | Details |
| --- | --- |
| Postman | Rufen Sie die [Postman-App](https://www.postman.com/downloads/) für Ihr Betriebssystem ab. Postman basic ist frei mit der Kontoerstellung. Postman ist zwar für die Verwendung von Adobe Target-APIs im Allgemeinen nicht erforderlich, erleichtert jedoch die Workflows der API und bietet mehrere Postman-Sammlungen an, um die Ausführung der APIs und deren Funktionsweise zu erleichtern. Der Rest dieses Tutorials geht von Arbeitskenntnissen des Postman aus. Hilfe erhalten Sie in der [Postman-Dokumentation](https://learning.getpostman.com/). |
| Verweise | Die Vertrautheit mit den folgenden Ressourcen wird während des gesamten Lernprogramms vorausgesetzt:<UL><li>[Adobe I/O Github](https://github.com/adobeio)</li><li>[Dokumentation zur Zielgruppe Adobe I/O](https://developers.adobetarget.com/api/#introduction)</li><li>[Recommendations API-Dokumentation](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[Nächste &quot;Verwalten des Recommendations-Katalogs&quot;>](manage-catalog.md)
