---
title: Verwendung von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Lernprogramm werden Benutzer den Datenanbietern vorgestellt. Erfahren Sie, wie Sie mit der Datenanbieterfunktion Daten von Drittanbietern einfach an Adobe Target weitergeben können.
role: Geschäftspraktiker, Entwickler
level: Erfahren
topic: Personalisierung, Integrationen
feature: Implementierung, Integrationen, APIs/SDKs
doc-type: feature video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 22%

---


# Datenanbieter zur Integration von Drittanbieterdaten in Adobe Target verwenden

[!UICONTROL Mit der Datenanbieterfunktion können Sie Dateien von Drittanbietern einfach an Target übergeben.  ]  Ein Drittanbieter kann ein Wetterdienst, ein DMP oder sogar Ihr eigener Web-Service sein. Anschließend können Sie diese Daten zur Erstellung von Zielgruppen und zielgerichtetem Inhalt und zur Aufwertung des Benutzerprofils verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Datenanbieter verwenden

1. Der Implementierungsexperte fügt Code vor &quot;at.js&quot;hinzu (oder im Abschnitt &quot;Bibliothekskopfzeile&quot;von &quot;at.js&quot;), der den API-Aufruf an den Drittanbieter ausführt, die Antwort analysiert und mit Name/Wert-Paaren aus der Antwort, die an [!DNL Target] gesendet werden soll, angibt.
1. &quot;at.js&quot;verwaltet Flackern und enthält die Name/Wert-Paare als benutzerdefinierte Parameter in der Anforderung zur globalen Zielgruppe.
1. Marketer erstellt Audiencen in der [!DNL Target]-Schnittstelle basierend auf diesen benutzerdefinierten Parametern.
1. Marketingexperten verwendet diese Audiencen zur Zielgruppe von Erlebnissen, Aktivitäten und Metriken sowie zur Audience von Berichten.

>[!NOTE]
>
>[!UICONTROL Datenanbieter ] benötigen at.js 1.3 oder höher

## Unterstützende Materialien

* [Datenanbieter in at.js und Adobe Target implementieren](implement-data-providers-to-integrate-third-party-data.md)
* [Dokumentation zu Datenanbietern](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)