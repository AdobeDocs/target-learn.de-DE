---
title: Wie funktioniert at.js 2.0?
description: at.js 2.0 erweitert die Unterstützung von Adobe Target für Single Page Applications (SPA) und integriert diese in andere Experience Cloud-Lösungen. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 7f037665-88a7-469c-8df5-c82cb0f65382
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Funktionsweise von at.js 2.0 in Adobe Target

`at.js` 2.0 erweitert die Unterstützung von Adobe Target für Single Page Applications (SPA) und integriert sich in andere Experience Cloud-Lösungen. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![Verhalten von at.js 2.0 beim Laden der Seite](assets/pageload.png)

1. Der Aufruf gibt die Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird die Kunden-ID durch einen weiteren Aufruf synchronisiert.

1. `at.js` Bibliothek wird synchron geladen und blendet den Hauptteil des Dokuments aus (`at.js` kann auch asynchron geladen werden, wobei ein optionales pre-hiding-Snippet auf der Seite implementiert ist).

1. Seitenladeanforderung erfolgt, einschließlich aller konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profilskripte werden ausgeführt und in die [!UICONTROL Profile Store] eingespeist. Der Store fordert qualifizierte Zielgruppen aus dem [!UICONTROL Audience Library] an (z. B. von [!DNL Analytics] freigegebene Zielgruppen, Audience Manager usw.). [!UICONTROL Customer Attributes] werden in einem Batch-Prozess an [!UICONTROL Profile Store] gesendet.
1. Basierend auf URL, Anfrageparametern und Profildaten entscheidet [!DNL Target], welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen

1. Zielgerichteter Inhalt, der an die Seite zurückgesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.

   Zielgerichtete Inhalte auf der aktuellen Seite werden so schnell wie möglich angezeigt, ohne dass der Standardinhalt flackert.

   Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Das `triggerView()` Verhalten finden Sie im nächsten Diagramm.)

1. [!DNL Analytics] von Daten, die von der Seite an die [!UICONTROL Data Collection] Server gesendet werden
1. [!DNL Target] Daten werden über die SDID mit Analytics-Daten abgeglichen und in den [!DNL Analytics]-Reporting-Speicher verarbeitet. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

![at.js 2.0-Verhalten, wenn die Funktion triggerView() verwendet wird](assets/triggerview.png)

1. `adobe.target.triggerView()` wird in der Einzelseitenanwendung aufgerufen
1. Zielgerichtete Inhalte für die Ansicht werden aus dem Cache gelesen

1. Zielgerichtete Inhalte werden so schnell wie möglich ohne Flimmern des Standardinhalts angezeigt

1. Eine Benachrichtigungsanfrage wird an die [!DNL Target] [!UICONTROL Profile Store] gesendet, um den Besucher in der Aktivitäts- und Inkrementmetrik zu zählen
1. [!DNL Analytics] Daten werden von der SPA an die [!UICONTROL Data Collection] gesendet

1. [!DNL Target] Daten werden vom [!DNL Target]-Backend an die [!UICONTROL Data Collection]-Server gesendet. [!DNL Target] Daten werden über die SDID mit [!DNL Analytics] Daten abgeglichen und in den [!DNL Analytics]-Reporting-Speicher verarbeitet. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

## Zusätzliche Ressourcen

* [Implementieren von at.js 2.0 in einer Einzelseitenanwendung](implement-atjs-20-in-a-single-page-application.md)
* [Verwenden des Visual Experience Composer von Adobe Target für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
