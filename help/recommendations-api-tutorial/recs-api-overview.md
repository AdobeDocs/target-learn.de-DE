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
source-git-commit: 542ff406fc24df54a2f1b007422492341ea46507
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# Übersicht über die Adobe Recommendations API

Zu den für [!DNL Recommendations] relevanten APIs zählen [Admin-APIs](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en), mit denen Sie:

* Verwalten Ihres Katalogs empfohlener Produkte oder Inhalte
* Verwalten Ihrer [!DNL Recommendations]-Algorithmen und -Aktivitäten

Mithilfe der Bereitstellungs-API [!DNL Target] [1} für Recommendations können Sie auch:](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en)

* Rufen Sie Empfehlungen in JSON-, HTML- oder XML-Objekten ab, damit sie im Web, auf Mobilgeräten, in E-Mails, im Internet der Dinge (IOT) und anderen Kanälen angezeigt werden können.

## Tutorial-Beschreibung

Dieses Tutorial führt Entwickler durch praktische Verfahren, mit denen sie [!DNL Recommendations]-APIs zum Konfigurieren und Verwalten von [!DNL Recommendations]-Katalogen und benutzerdefinierten Kriterien sowie zur Verwendung der Bereitstellungs-API zum Abrufen von Empfehlungsinhalten verwenden. Am Ende dieses Tutorials können Sie:

* Konfigurieren und Verwalten von Entitäten mithilfe der Recommendations-API
* Benutzerdefinierte Kriterien mithilfe der Recommendations-API konfigurieren und verwalten
* Erfahren Sie, wie Sie Recommendations mit der Bereitstellungs-API verwenden, um Empfehlungsergebnisse auf Nicht-HTML-Geräten zu verwenden.

## Zielgruppe

Dieses Tutorial richtet sich an Entwickler, die mit Target-APIs oder Recommendations-APIs neu sind.

## Voraussetzungen

Für die Verwendung der Target-Admin-APIs ist die Einrichtung der Adobe-Authentifizierung ](https://experienceleague.adobe.com/docs/target-dev/developer/api/configure-authentication.html?lang=de){target="_blank"} erforderlich. [ Stellen Sie vor Beginn dieses Tutorials sicher, dass Sie diese Konfiguration vorgenommen haben.

## Ressourcen

Beachten Sie die folgenden Ressourcen, die zum Verständnis dieses Tutorials und zum erfolgreichen Befolgen dieses Tutorials erforderlich sind:

| Ressource | Details |
| --- | --- |
| Postman | Rufen Sie die [Postman-App](https://www.postman.com/downloads/) für Ihr Betriebssystem ab. Postman Basic ist mit der Kontoerstellung kostenlos. Postman ist zwar nicht erforderlich, um Adobe Target-APIs im Allgemeinen zu verwenden, erleichtert aber API-Workflows. Adobe Target bietet mehrere Postman-Sammlungen, die die Ausführung seiner APIs erleichtern und erfahren, wie sie funktionieren. Der Rest dieses Tutorials setzt Grundkenntnisse in Postman voraus. Hilfe finden Sie in der [Postman-Dokumentation](https://learning.getpostman.com/). |
| Verweise | Die Vertrautheit mit den folgenden Ressourcen wird im Rest dieses Tutorials vorausgesetzt:<UL><li>[Adobe I/O Github](https://github.com/adobeio)</li><li>[Adobe I/O-Dokumentation für Target](https://developers.adobetarget.com/api/#introduction)</li><li>[Recommendations API-Dokumentation](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[Weiter mit &quot;Verwalten des Recommendations-Katalogs&quot;>](https://experienceleague.adobe.com/docs/target-dev/developer/api/recommendations-api/manage-catalog.html){target="_blank"}
