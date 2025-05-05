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
source-git-commit: fcd2273ba373dc2b3bc59a77f1925cdb7b2ed3ee
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen mit Adobe Target

Mit Antwort-Token und `at.js` benutzerspezifischen Ereignissen können Sie Profilinformationen von [!DNL Target] an Drittanbietersysteme weitergeben. Jedes Objekt im [!DNL Target] Besucherprofil, einschließlich benutzerdefinierter Profilattribute, geografischer Informationen, Aktivitätsdetails und integrierter Profile, kann der [!DNL Target]-Antwort hinzugefügt werden, in der Sie benutzerdefinierte JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/33825/?quality=12&captions=ger)

## Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen

1. Bestimmen Sie, welche Daten Sie aus [!DNL Target] benötigen
1. Aktivieren Sie die Antwort-Token für die benötigten Daten, indem Sie den Umschalter im Bildschirm Setup->Antwort-Token umschalten.
1. Bestimmen, welchen Ereignis-Listener Sie verwenden müssen
1. Schreiben Sie die JavaScript, die erforderlich ist, um auf das Adobe Target-Ereignis zu warten, die Antwort-Token zu lesen und das zu tun, was Sie für Ihre Integration benötigen
1. Stellen Sie Ihren Ereignis-Listener JavaScript mit einer benutzerdefinierten Codeaktion in Launch nach der Aktion „Target laden“ bereit oder fügen Sie ihn im Bildschirm „Setup->Implementierung“ von at.js zum Abschnitt „Bibliotheksfußzeile“ hinzu und speichern Sie eine neue Datei „at.js“
1. QA und Veröffentlichen der Integration

## Zusätzliche Ressourcen

* [Verwenden von Experience Cloud Debugger mit Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zum Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=de)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)
