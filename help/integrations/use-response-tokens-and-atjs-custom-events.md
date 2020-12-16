---
title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target
seo-title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target
description: Mithilfe von Antwort-Tokens und benutzerdefinierten at.js-Ereignissen können Sie Profil-Informationen von der Zielgruppe an Drittanbietersysteme weitergeben. Jedes Objekt im Zielgruppe Besucher-Profil, einschließlich der Attribute benutzerdefinierter Profil, der geografischen Informationen, der Details der Aktivität und der integrierten Profil, kann der Zielgruppe hinzugefügt werden, in der Sie benutzerdefiniertes JavaScript zur Integration mit einem Drittanbieter verwenden können.
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

Antwort-Token und benutzerspezifische Ereignis ermöglichen es Ihnen, Profil-Informationen von `at.js` für Drittanbietersysteme freizugeben. [!DNL Target] Jedes Objekt im Profil [!DNL Target], einschließlich benutzerdefinierter Profil-Attribute, geografischer Informationen, Details zur Aktivität und integrierter Profil, kann der Antwort [!DNL Target] hinzugefügt werden, in der Sie benutzerdefiniertes JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Verwenden benutzerdefinierter Ereignis für Antwort-Token und at.js

1. Bestimmen Sie, welche Daten Sie von [!DNL Target] benötigen.
1. Aktivieren Sie die AntwortToken für die benötigten Daten, indem Sie den Umschalter im Bildschirm &quot;Setup->Antwort-Token&quot;umschalten
1. Bestimmen des zu verwendenden Ereignis-Listeners
1. Schreiben Sie das erforderliche JavaScript, um auf das Adobe Target-Ereignis zu hören, lesen Sie die Antwort-Token und tun Sie, was Sie für Ihre Integration benötigen
1. Stellen Sie Ihr Ereignis-Listener-JavaScript mit einer benutzerdefinierten Codeaktion beim Start nach der Aktion &quot;Zielgruppe laden&quot;bereit oder fügen Sie es im Bildschirm &quot;Einstellungen&quot;> &quot;Implementierung&quot;im Abschnitt &quot;Bibliotheksfußzeile&quot;von &quot;at.js&quot;hinzu und speichern Sie eine neue at.js-Datei
1. Qualitätssicherung und Veröffentlichung der Integration

## Zusätzliche Ressourcen

* [Verwenden des Experience Cloud Debuggers mit Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zum Antwort-Token](https://docs.adobe.com/help/en/target/using/administer/response-tokens.html)
* [Dokumentation zu benutzerspezifischen at.js-Ereignissen](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/atjs-custom-events.html)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)