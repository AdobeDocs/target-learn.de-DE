---
title: Datenanbieter zur Integration von Drittanbieterdaten in Adobe Target verwenden
seo-title: Datenanbieter zur Integration von Drittanbieterdaten in Adobe Target verwenden
description: Mit der Datenanbieterfunktion können Sie Dateien von Drittanbietern einfach an Target übergeben.  Ein Drittanbieter kann ein Wetterdienst, ein DMP oder sogar Ihr eigener Web-Service sein. Anschließend können Sie diese Daten zur Erstellung von Zielgruppen und zielgerichtetem Inhalt und zur Aufwertung des Benutzerprofils verwenden.
audience: marketer
difficulty: 5
author: Daniel Wright
doc-type: use
activity-type: feature-video
translation-type: tm+mt
source-git-commit: b331bb29c099bd91df27300ebe199cafa12516db
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 40%

---


# Datenanbieter zur Integration von Drittanbieterdaten in Adobe Target verwenden

[!UICONTROL Mit der Datenanbieterfunktion können Sie Dateien von Drittanbietern einfach an Target übergeben.  ]  Ein Drittanbieter kann ein Wetterdienst, ein DMP oder sogar Ihr eigener Web-Service sein. Anschließend können Sie diese Daten zur Erstellung von Zielgruppen und zielgerichtetem Inhalt und zur Aufwertung des Benutzerprofils verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Datenanbieter verwenden

1. Der Implementierungsexperte fügt Code vor &quot;at.js&quot;hinzu (oder im Abschnitt &quot;Bibliothekskopfzeile&quot;von &quot;at.js&quot;), der den API-Aufruf an den Drittanbieter ausführt, die Antwort analysiert und mit Name/Wert-Paaren aus der Antwort, die an gesendet werden soll, angibt. [!DNL Target]
1. at.js verwaltet Flackern und enthält die Namen/Werte-Paare als benutzerdefinierte Parameter in der globalen Target-Anforderung.
1. Marketer erstellt Audiencen auf der [!DNL Target] Oberfläche basierend auf diesen benutzerdefinierten Parametern.
1. Marketingexperten verwendet diese Audiencen zur Zielgruppe von Erlebnissen, Aktivitäten und Metriken sowie zur Audience von Berichten.

>[!NOTE]
>
>[!UICONTROL Datenanbieter] benötigen at.js 1.3 oder höher

## Unterstützende Materialien

* [Datenanbieter in at.js und Adobe Target implementieren](implement-data-providers-to-integrate-third-party-data.md)
* [Dokumentation zu Datenanbietern](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)