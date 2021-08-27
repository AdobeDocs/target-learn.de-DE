---
title: Verwenden von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Tutorial erfahren Sie, wie Benutzer Datenanbietern vorgestellt werden. Erfahren Sie, wie Sie mit der Datenanbieter-Funktion Daten von Drittanbietern einfach an Adobe Target weitergeben können.
role: User, Developer
level: Experienced
topic: Personalization, Integrations
feature: Implementation, Integrations, APIs/SDKs
doc-type: feature video
kt: null
thumbnail: null
author: Daniel Wright
exl-id: 1892136e-14e3-4e52-8b1f-aee806d2f83a
source-git-commit: d1517f0763290eb61a9e4eef4f2eb215a9cdd667
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 23%

---

# Verwenden von Datenanbietern zur Integration von Drittanbieterdaten in Adobe Target

[!UICONTROL Mit der Datenanbieterfunktion können Sie Dateien von Drittanbietern einfach an Target übergeben.  ]  Ein Drittanbieter kann ein Wetterdienst, ein DMP oder sogar Ihr eigener Web-Service sein. Anschließend können Sie diese Daten zur Erstellung von Zielgruppen und zielgerichtetem Inhalt und zur Aufwertung des Benutzerprofils verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/22349/?quality=12)

## Verwenden von Datenanbietern

1. Der Implementierungsexperte fügt Code vor at.js (oder im Abschnitt &quot;Bibliothekskopfzeile&quot;von at.js) hinzu, der den API-Aufruf an den Drittanbieter sendet, die Antwort analysiert und mit Name/Wert-Paaren aus der Antwort angibt, die an [!DNL Target] gesendet werden.
1. at.js verwaltet Flackern und schließt die Name/Wert-Paare als benutzerdefinierte Parameter in die globale Target-Anforderung ein.
1. Marketer erstellt Zielgruppen in der [!DNL Target]-Schnittstelle basierend auf diesen benutzerdefinierten Parametern.
1. Marketingexperten verwenden diese Zielgruppen für Erlebnisse, Aktivitäten und Metriken sowie für Berichterstellungszielgruppen.

>[!NOTE]
>
>[!UICONTROL Datenanbieter erfordert ] at.js 1.3 oder höher

## Unterstützende Materialien

* [Implementieren von Datenanbietern in at.js und Adobe Target](implement-data-providers-to-integrate-third-party-data.md)
* [Dokumentation zu Datenanbietern](https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/at-js-implementation/functions-overview/targetgobalsettings.html?lang=en#data-providers)
