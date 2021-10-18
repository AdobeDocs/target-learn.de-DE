---
title: Was ist die Adobe Recommendations-API?
description: Dieses Tutorial führt Entwickler durch praktische Verfahren zur Verwendung der Adobe Target Recommendations-APIs zum Konfigurieren und Verwalten von Recommendations-Katalogen und benutzerdefinierten Kriterien sowie zur Verwendung der Bereitstellungs-API zum Abrufen von Empfehlungsinhalten.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration, Overview
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 10f80056-fb71-4362-86bc-d161f596cb91
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 3%

---

# Übersicht über die Adobe Recommendations API

Zu den für [!DNL Recommendations] relevanten APIs gehören [Admin-APIs](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en), mit denen Sie:

* Verwalten Ihres Katalogs empfohlener Produkte oder Inhalte
* Verwalten Ihrer [!DNL Recommendations]-Algorithmen und -Aktivitäten

Mithilfe der [!DNL Target] [Bereitstellungs-API](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en) mit Recommendations können Sie auch:

* Rufen Sie Empfehlungen in JSON-, HTML- oder XML-Objekten ab, damit sie im Web, auf Mobilgeräten, in E-Mails, im Internet der Dinge (IOT) und anderen Kanälen angezeigt werden können.

## Tutorial-Beschreibung

Dieses Tutorial führt Entwickler durch praktische Verfahren, mit denen die [!DNL Recommendations]-APIs zum Konfigurieren und Verwalten von [!DNL Recommendations]-Katalogen und benutzerdefinierten Kriterien sowie zur Verwendung der Bereitstellungs-API zum Abrufen von Empfehlungsinhalten verwendet werden. Am Ende dieses Tutorials können Sie:

* Konfigurieren und Verwalten von Entitäten mithilfe der Recommendations-API
* Benutzerdefinierte Kriterien mithilfe der Recommendations-API konfigurieren und verwalten
* Erfahren Sie, wie Sie Recommendations mit der Bereitstellungs-API verwenden, um Empfehlungsergebnisse auf Nicht-HTML-Geräten zu verwenden.

## Zielgruppe

Dieses Tutorial richtet sich an Entwickler, die mit Target-APIs oder Recommendations-APIs neu sind.

## Voraussetzungen

Für die Verwendung der Target Admin-APIs ist [Einrichtung der Adobe-Authentifizierung](../apis/configure-io-target-integration.md) erforderlich. Stellen Sie vor Beginn dieses Tutorials sicher, dass Sie diese Konfiguration vorgenommen haben.

## Ressourcen

Beachten Sie die folgenden Ressourcen, die zum Verständnis dieses Tutorials und zum erfolgreichen Befolgen dieses Tutorials erforderlich sind:

| Ressource | Details |
| --- | --- |
| Postman | Rufen Sie die [Postman-App](https://www.postman.com/downloads/) für Ihr Betriebssystem ab. Postman basic ist mit der Kontoerstellung kostenlos. Postman ist zwar nicht erforderlich, um Adobe Target-APIs im Allgemeinen zu verwenden, erleichtert jedoch API-Workflows und Adobe Target bietet mehrere Postman-Sammlungen, mit denen die APIs ausgeführt und ihre Funktionsweise erklärt werden können. Der Rest dieses Tutorials setzt Arbeitskenntnisse in Postman voraus. Hilfe erhalten Sie in der [Postman-Dokumentation](https://learning.getpostman.com/). |
| Verweise | Die Vertrautheit mit den folgenden Ressourcen wird im Rest dieses Tutorials vorausgesetzt:<UL><li>[Adobe I/O Github](https://github.com/adobeio)</li><li>[Dokumentation zur Target-Adobe I/O](https://developers.adobetarget.com/api/#introduction)</li><li>[Dokumentation zur Recommendations API](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[Weiter mit &quot;Verwalten des Recommendations-Katalogs&quot;>](manage-catalog.md)
