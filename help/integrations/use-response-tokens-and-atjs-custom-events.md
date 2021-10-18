---
title: Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen
description: Erfahren Sie, wie Sie mithilfe von Antwort-Token und benutzerspezifischen at.js-Ereignissen Profilinformationen aus Target für Drittanbietersysteme freigeben können.
role: Developer
level: Experienced
topic: Personalization, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: d6ce5367-a453-4e6c-8545-9fa676977f04
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 3%

---

# Verwenden von Antwort-Token und benutzerspezifischen at.js-Ereignissen mit Adobe Target

Antwort-Token und `at.js` Benutzerdefinierte Ereignisse ermöglichen es Ihnen, Profilinformationen von [!DNL Target] für Drittanbietersysteme freizugeben. Jedes Objekt im Besucherprofil [!DNL Target], einschließlich benutzerdefinierter Profilattribute, geografischer Informationen, Aktivitätsdetails und integrierter Profile, kann der Antwort [!DNL Target] hinzugefügt werden, in der Sie benutzerdefiniertes JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen

1. Bestimmen Sie, welche Daten Sie von [!DNL Target] benötigen
1. Aktivieren Sie die Antwort-Token für die benötigten Daten, indem Sie den Umschalter im Bildschirm &quot;Setup->Antwort-Token&quot;aktivieren.
1. Bestimmen, welcher Ereignis-Listener verwendet werden muss
1. Schreiben Sie das erforderliche JavaScript, um auf das Adobe Target-Ereignis zu warten, die Antwort-Token zu lesen und die für Ihre Integration erforderlichen Maßnahmen zu ergreifen
1. Stellen Sie Ihr Ereignis-Listener-JavaScript nach der Aktion &quot;Target laden&quot;mithilfe einer benutzerdefinierten Code-Aktion in Launch bereit oder fügen Sie es im Bildschirm &quot;Setup->Implementierung&quot;im Abschnitt &quot;Bibliotheksfußzeile von at.js&quot;hinzu und speichern Sie eine neue at.js-Datei.
1. Qualitätssicherung und Veröffentlichung der Integration

## Zusätzliche Ressourcen

* [Verwenden des Experience Cloud Debuggers mit Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zu Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=en)
* [Dokumentation zu benutzerspezifischen at.js-Ereignissen](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js-implementation/functions-overview/atjs-custom-events.html?lang=en)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)
