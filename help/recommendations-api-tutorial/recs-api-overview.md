---
title: Was ist die Adobe Recommendations-API?
description: Dieses Tutorial führt Entwicklerinnen und Entwicklern durch die praktische Verwendung der Adobe Target Recommendations-APIs zum Konfigurieren und Verwalten von Recommendations-Katalogen und benutzerdefinierten Kriterien sowie die Verwendung der Bereitstellungs-API zum Abrufen von Recommendations-Inhalten.
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

# Übersicht über die Adobe Recommendations-API

Zu den für [!DNL Recommendations] relevanten APIs gehören [Admin-](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en)), mit denen Sie:

* Katalog mit empfohlenen Produkten oder Inhalten verwalten
* Verwalten von [!DNL Recommendations] und Aktivitäten

Mithilfe der [!DNL Target]Bereitstellungs[API](https://experienceleague.adobe.com/docs/target/using/apis/api-overview.html?lang=en) mit Recommendations können Sie auch:

* Rufen Sie Empfehlungen in JSON-, HTML- oder XML-Objekten ab, damit sie in Web-, Mobile-, E-Mail-, Internet der Dinge (IOT) und anderen Kanälen angezeigt werden können.

## Tutorial-Beschreibung

Dieses Tutorial führt Entwicklerinnen und Entwicklern durch die praktische Verwendung der [!DNL Recommendations]-APIs zum Konfigurieren und Verwalten von [!DNL Recommendations] und benutzerdefinierten Kriterien sowie die Verwendung der Bereitstellungs-API zum Abrufen von Recommendations-Inhalten. Am Ende dieses Tutorials werden Sie zu Folgendem in der Lage sein:

* Konfigurieren und Verwalten von Entitäten mit der Recommendations-API
* Konfigurieren und Verwalten benutzerdefinierter Kriterien mithilfe der Recommendations-API
* Erfahren Sie, wie Sie Recommendations mit der Bereitstellungs-API verwenden können, um Recommendations-Ergebnisse auf Nicht-HTML-Geräten zu verwenden

## Zielgruppe

Dieses Tutorial richtet sich an Entwicklerinnen und Entwickler, die noch nicht mit Target-APIs oder Recommendations-APIs vertraut sind.

## Voraussetzungen

Die Verwendung der Target-Admin-APIs erfordert die Einrichtung der [Adobe-Authentifizierung](https://experienceleague.adobe.com/docs/target-dev/developer/api/configure-authentication.html?lang=de){target="_blank"}. Vergewissern Sie sich, dass Sie dies konfiguriert haben, bevor Sie mit diesem Tutorial beginnen.

## Ressourcen

Beachten Sie die folgenden Ressourcen, die erforderlich sind, um dieses Tutorial zu verstehen, und folgen Sie ihm erfolgreich:

| Ressource | Details |
| --- | --- |
| Postman | Rufen Sie die [Postman](https://www.postman.com/downloads/)App für Ihr Betriebssystem ab. Postman Basic ist bei der Kontoerstellung kostenlos. Obwohl dies für die Verwendung von Adobe Target-APIs im Allgemeinen nicht erforderlich ist, erleichtert Postman API-Workflows und Adobe Target bietet mehrere Postman-Sammlungen, die die Ausführung seiner APIs und deren Funktionsweise erleichtern. Für den Rest dieses Tutorials werden Kenntnisse über Postman vorausgesetzt. Unterstützung erhalten Sie in der [Dokumentation zu Postman](https://learning.getpostman.com/). |
| Verweise | Im weiteren Verlauf dieses Tutorials wird von der Vertrautheit mit den folgenden Ressourcen ausgegangen:<UL><li>[Adobe I/O GitHub](https://github.com/adobeio)</li><li>[Target Adobe I/O-Dokumentation](https://developers.adobetarget.com/api/#introduction)</li><li>[Dokumentation zur Recommendations-API](https://developers.adobetarget.com/api/recommendations/)</li></ul> |

[Weiter &quot;Recommendations-Katalog verwalten“ >](https://experienceleague.adobe.com/docs/target-dev/developer/api/recommendations-api/manage-catalog.html){target="_blank"}
