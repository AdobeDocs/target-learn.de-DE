---
title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target
seo-title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target
description: Mithilfe von Antwort-Tokens und benutzerdefinierten at.js-Ereignissen können Sie Profil-Informationen von Target an Drittanbietersysteme weitergeben. Jedes Objekt im Target Besucher-Profil, einschließlich benutzerdefinierter Profil-Attribute, geografischer Informationen, Aktivitäten-Details und integrierter Profil, kann der Target-Antwort hinzugefügt werden, in der Sie benutzerdefiniertes JavaScript zur Integration mit einem Drittanbieter verwenden können.
audience: developer
difficulty: 5
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 2%

---


# Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target

Antwort-Token und `at.js` benutzerdefinierte Ereignis ermöglichen Ihnen die Freigabe von Profil-Informationen von [!DNL Target] zu Drittanbietersystemen. Jedes Objekt im [!DNL Target] [!DNL Target] Besucher-Profil, einschließlich der Attribute benutzerdefinierter Profil, der geografischen Informationen, der Details der Aktivität und der integrierten Profil, kann der Antwort hinzugefügt werden, sodass Sie benutzerdefiniertes JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Verwenden benutzerdefinierter Ereignis für Antwort-Token und at.js

1. Bestimmen Sie, aus welchen Daten Sie wählen möchten [!DNL Target]
1. Aktivieren Sie die AntwortToken für die benötigten Daten, indem Sie den Umschalter im Bildschirm &quot;Setup->Antwort-Token&quot;umschalten
1. Bestimmen des zu verwendenden Ereignis-Listeners
1. Schreiben Sie das erforderliche JavaScript, um auf das Adobe Target-Ereignis zu hören, die Antwort-Token zu lesen und Ihre Integrationsanforderungen zu erfüllen
1. Stellen Sie Ihr Ereignis-Listener-JavaScript mit einer benutzerdefinierten Codeaktion in &quot;Start&quot;nach der Aktion &quot;Target laden&quot;bereit oder fügen Sie es im Bildschirm &quot;Einstellungen&quot;> &quot;Implementierung&quot;im Abschnitt &quot;at.js&quot;zur Bibliotheksfußzeile hinzu und speichern Sie eine neue at.js-Datei
1. Qualitätssicherung und Veröffentlichung der Integration

## Zusätzliche Ressourcen

* [Experience Cloud-Debugger mit Adobe Target verwenden](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zum Antwort-Token](https://docs.adobe.com/help/en/target/using/administer/response-tokens.html)
* [Dokumentation zu benutzerspezifischen at.js-Ereignissen](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/atjs-custom-events.html)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)