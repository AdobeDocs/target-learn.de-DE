---
title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen
description: Erfahren Sie, wie Sie mit Antwort-Token und benutzerdefinierten at.js-Ereignissen Profilinformationen von Target an Drittanbietersysteme weitergeben können.
role: Developer
level: Experienced
topic: Personalization, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: d6ce5367-a453-4e6c-8545-9fa676977f04
TQID: https://experienceleague.adobe.com/gJfFi9mC3iKY8pEdvE1Tuk7Mk2rUOdTKtv67vXQwkO8
product_v2: id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2: id: c93393a4-e558-47e1-992e-c91ed4d480ceid: f7c7de77-382f-4f48-8b36-61a170f06d3d
subfeature_v2: id: fd0ff162-b6d3-4a11-8aeb-e165a01c0f0a
role_v2: id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: c1579802-ddd4-4214-8a91-97b2066abe11id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 230
ht-degree: 3%

---

# Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target

Mit Antwort-Token und `at.js` benutzerspezifischen Ereignissen können Sie Profilinformationen von [!DNL Target] an Drittanbietersysteme weitergeben. Jedes Objekt im [!DNL Target] Besucherprofil, einschließlich benutzerdefinierter Profilattribute, geografischer Informationen, Aktivitätsdetails und integrierter Profile, kann der [!DNL Target]-Antwort hinzugefügt werden, in der Sie benutzerdefinierte JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen

1. Bestimmen Sie, welche Daten Sie aus [!DNL Target] benötigen
1. Aktivieren Sie die Antwort-Token für die benötigten Daten, indem Sie den Umschalter im Bildschirm Setup->Antwort-Token umschalten.
1. Bestimmen, welchen Ereignis-Listener Sie verwenden müssen
1. Schreiben Sie die JavaScript, die erforderlich ist, um auf das Adobe Target-Ereignis zu warten, die Antwort-Token zu lesen und das zu tun, was Sie für Ihre Integration benötigen
1. Stellen Sie Ihren Ereignis-Listener JavaScript mit einer benutzerdefinierten Codeaktion in Launch nach der Aktion „Target laden“ bereit oder fügen Sie ihn im Bildschirm „Setup->Implementierung“ von at.js zum Abschnitt „Bibliotheksfußzeile“ hinzu und speichern Sie eine neue Datei „at.js“
1. QA und Veröffentlichen der Integration

## Zusätzliche Ressourcen

* [Verwenden von Experience Cloud Debugger mit Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zu Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=en)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)
