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
source-git-commit: 0ecfde208b3e201de135512d5aab70192fc2b826
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 3%

---

# Übersicht über die Adobe Recommendations API

Für [!DNL Recommendations] include [Admin-APIs](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en) mit denen Sie:

* Verwalten Ihres Katalogs empfohlener Produkte oder Inhalte
* Verwalten Sie Ihre [!DNL Recommendations] Algorithmen und Aktivitäten

Verwenden der [!DNL Target] [Bereitstellungs-API](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en) Mit Recommendations können Sie auch:

* Rufen Sie Empfehlungen in JSON-, HTML- oder XML-Objekten ab, damit sie im Web, auf Mobilgeräten, in E-Mails, im Internet der Dinge (IOT) und anderen Kanälen angezeigt werden können.

## Tutorial-Beschreibung

Dieses Tutorial führt Entwickler durch eine praktische Vorgehensweise mit dem [!DNL Recommendations] APIs zum Konfigurieren und Verwalten [!DNL Recommendations] Kataloge und benutzerdefinierte Kriterien sowie die Verwendung der Bereitstellungs-API zum Abrufen von Empfehlungsinhalten. Am Ende dieses Tutorials können Sie:

* Konfigurieren und Verwalten von Entitäten mithilfe der Recommendations-API
* Benutzerdefinierte Kriterien mithilfe der Recommendations-API konfigurieren und verwalten
* Erfahren Sie, wie Sie Recommendations mit der Bereitstellungs-API verwenden, um Empfehlungsergebnisse auf Nicht-HTML-Geräten zu verwenden.

## Zielgruppe

Dieses Tutorial richtet sich an Entwickler, die mit Target-APIs oder Recommendations-APIs neu sind.

## Voraussetzungen

Die Verwendung der Target Admin-APIs erfordert [Einrichtung der Adobe-Authentifizierung](https://developer.adobe.com/target/before-administer/configure-authentication/){target=_blank}. Stellen Sie vor Beginn dieses Tutorials sicher, dass Sie diese Konfiguration vorgenommen haben.

## Ressourcen

Beachten Sie die folgenden Ressourcen, die zum Verständnis dieses Tutorials und zum erfolgreichen Befolgen dieses Tutorials erforderlich sind:

| Ressource | Details |
| --- | --- |
| Postman | Rufen Sie die [Postman-App](https://www.postman.com/downloads/) für Ihr Betriebssystem. Postman Basic ist mit der Kontoerstellung kostenlos. Postman ist zwar nicht erforderlich, um Adobe Target-APIs im Allgemeinen zu verwenden, erleichtert aber API-Workflows. Adobe Target bietet mehrere Postman-Sammlungen, die die Ausführung seiner APIs erleichtern und erfahren, wie sie funktionieren. Der Rest dieses Tutorials setzt Grundkenntnisse in Postman voraus. Informationen zur Unterstützung finden Sie im Abschnitt [Postman-Dokumentation](https://learning.getpostman.com/). |
| Verweise | Die Vertrautheit mit den folgenden Ressourcen wird im Rest dieses Tutorials vorausgesetzt:<UL><li>[Adobe I/O Github](https://github.com/adobeio)</li><li>[Dokumentation zur Target-Adobe I/O](https://developers.adobetarget.com/api/#introduction)</li><li>[Dokumentation zur Recommendations API](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[Weiter mit &quot;Verwalten des Recommendations-Katalogs&quot;>](https://developer.adobe.com/target/before-administer/recs-api/manage-catalog/){target=_blank}
