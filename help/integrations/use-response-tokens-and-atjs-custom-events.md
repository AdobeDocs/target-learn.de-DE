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
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Verwenden von Antwort-Token und benutzerspezifischen at.js-Ereignissen mit Adobe Target

Antwort-Token und `at.js` Benutzerspezifische Ereignisse ermöglichen es Ihnen, Profilinformationen von [!DNL Target] an Drittanbietersysteme zu teilen. Jedes Objekt im Besucherprofil [!DNL Target], einschließlich benutzerdefinierter Profilattribute, geografischer Informationen, Aktivitätsdetails und integrierter Profile, kann der Antwort [!DNL Target] hinzugefügt werden, in der Sie benutzerdefinierte JavaScript zur Integration mit einem Drittanbieter verwenden können.

>[!VIDEO](https://video.tv.adobe.com/v/23253/?quality=12)

## Verwenden von Antwort-Token und benutzerdefinierten at.js-Ereignissen

1. Bestimmen Sie, welche Daten Sie von [!DNL Target] benötigen
1. Aktivieren Sie die Antwort-Token für die benötigten Daten, indem Sie den Umschalter im Bildschirm &quot;Setup->Antwort-Token&quot;aktivieren.
1. Bestimmen, welcher Ereignis-Listener verwendet werden muss
1. Schreiben Sie die JavaScript, die erforderlich ist, um auf das Adobe Target-Ereignis zu warten, lesen Sie die Antwort-Token und tun Sie, was Sie für Ihre Integration benötigen
1. Stellen Sie Ihren Ereignis-Listener JavaScript mithilfe einer benutzerdefinierten Code-Aktion in Launch nach der Aktion &quot;Target laden&quot;bereit oder fügen Sie ihn im Bildschirm &quot;Setup->Implementierung&quot;im Abschnitt &quot;Bibliotheksfußzeile von at.js&quot;hinzu und speichern Sie eine neue at.js-Datei.
1. Qualitätssicherung und Veröffentlichung der Integration

## Zusätzliche Ressourcen

* [Verwenden des Experience Cloud Debuggers mit Adobe Target](../troubleshooting/troubleshoot-with-the-experience-cloud-debugger.md)
* [Dokumentation zum Antwort-Token](https://experienceleague.adobe.com/docs/target/using/administer/response-tokens.html?lang=en)
* [Verwenden von Datenanbietern in Adobe Target](use-data-providers-to-integrate-third-party-data.md)
