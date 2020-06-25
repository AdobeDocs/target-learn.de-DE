---
title: Implementieren von Datenanbietern zur Integration von Drittanbieterdaten in Adobe Target
seo-title: Implementieren von Datenanbietern zur Integration von Drittanbieterdaten in Adobe Target
description: Implementierungsdetails und Beispiele für die Verwendung der Data Providers-Funktion von Adobe Target zum Abrufen von Daten von Drittanbietern und zum Übergeben dieser Daten in die Target-Anforderung.
audience: developer
difficulty: 5
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 0%

---


# Implementieren von [!UICONTROL Datenanbietern] zur Integration von Drittanbieterdaten in Adobe Target

Implementation details and examples of how to use Adobe Target&#39;s [!UICONTROL Data Providers] feature to retrieve data from third-party data providers and pass it in the Target request.

>[!NOTE]
>
>[!UICONTROL Datenanbieter] benötigen `at.js` 1.3 oder höher

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

Minimieren Sie die Auswirkungen auf die Seitenladezeit, indem Sie Daten in einem Sitzungsobjekt speichern. Alternativ dazu können Sie die Werte als Profil-Parameter mit dem `profile.` Präfix übergeben und sie einfach in der ersten [!DNL Target] Anforderung der Sitzung weitergeben. Sie sind jedoch auf die Übergabe von 50 Profil-Parametern pro Anforderung beschränkt.

Ein funktionierendes Beispiel mit dem im Video verwendeten Code finden Sie hier: [https://target.enablementadobe.com/data-providers/reducedCalls.html](https://target.enablementadobe.com/data-providers/reducedCalls.html)

## Unterstützende Materialien

* [Datenanbieter mit Adobe Target verwenden](use-data-providers-to-integrate-third-party-data.md)

* [Dokumentation zu Datenanbietern](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/functions-overview/targetgobalsettings.html#data-providers)