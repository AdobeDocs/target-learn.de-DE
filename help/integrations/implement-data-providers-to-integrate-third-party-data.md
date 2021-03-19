---
title: Implementieren von Datenanbietern zur Integration von Drittanbieterdaten
description: In diesem Lernprogramm werden Implementierungsdetails und Beispiele für die Verwendung der Adobe Target Data Providers-Funktion zum Abrufen von Daten von Drittanbietern und zum Übermitteln dieser Daten in die Zielgruppe-Anforderung erläutert.
role: Entwickler
level: Erfahren
topic: Personalisierung, Integrationen
feature: Implementierung, Integrationen, APIs/SDKs
doc-type: technical video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# [!UICONTROL Datenanbieter] implementieren, um Daten von Drittanbietern in Adobe Target zu integrieren

Implementierungsdetails und Beispiele für die Verwendung der Adobe Target-Funktion [!UICONTROL Datenanbieter] zum Abrufen von Daten von Drittanbietern und zum Übergeben dieser Daten in die Zielgruppe-Anforderung.

>[!NOTE]
>
>[!UICONTROL Datenanbieter ] erfordern  `at.js` 1.3 oder höher

## Implementieren der grundlegenden Komponenten von Datenanbietern

>[!VIDEO](https://video.tv.adobe.com/v/22348/?quality=12)

Eine schnelle Übersicht über die grundlegenden Komponenten eines `dataProvider` und wie Sie Ihren Code in der richtigen Reihenfolge bekommen.\
Ein funktionierendes Beispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/simple.html](https://target.enablementadobe.com/data-providers/simple.html)

## Integration mit einer Drittanbieter-API

>[!VIDEO](https://video.tv.adobe.com/v/22345/)

Ein realistischeres Beispiel für die Integration einer Wetter-API.\
Ein funktionierendes Beispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/3rdparty.html](https://target.enablementadobe.com/data-providers/3rdparty.html)

## Integration mit mehreren Anbietern

>[!VIDEO](https://video.tv.adobe.com/v/22346/)

So integrieren Sie Daten von mehreren Anbietern in Ihre globale [!DNL Target] Anforderung.\
Ein funktionierendes Beispiel mit dem im Video verwendeten Code finden Sie hier:
[https://target.enablementadobe.com/data-providers/combined.html](https://target.enablementadobe.com/data-providers/combined.html)

## Auswirkungen des Seitenladevorgangs minimieren

>[!VIDEO](https://video.tv.adobe.com/v/22347/)

Minimieren Sie die Auswirkungen auf die Seitenladezeit, indem Sie Daten in einem Sitzungsobjekt speichern. Alternativ können Sie die Werte als Profil-Parameter mit dem Präfix `profile.` übergeben und sie einfach in der ersten [!DNL Target]-Anforderung der Sitzung weitergeben. Sie sind jedoch auf die Übergabe von 50 Profil-Parametern pro Anforderung beschränkt.

Ein funktionierendes Beispiel mit dem im Video verwendeten Code finden Sie hier: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Unterstützende Materialien

* [Datenanbieter mit Adobe Target verwenden](use-data-providers-to-integrate-third-party-data.md)

* [Dokumentation zu Datenanbietern](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)