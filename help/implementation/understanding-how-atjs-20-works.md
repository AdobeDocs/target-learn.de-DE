---
title: Wie funktioniert at.js 2.0?
description: at.js 2.0 verbessert die Unterstützung von Adobe Target für Einzelseitenanwendungen (SPA) und kann mit anderen Experience Cloud-Lösungen integriert werden. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.
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

# Funktionsweise von Adobe Target at.js 2.0

`at.js` 2.0 verbessert die Unterstützung von Adobe Target für Einzelseitenanwendungen (SPA) und kann mit anderen Experience Cloud-Lösungen integriert werden. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![Verhalten von at.js 2.0 beim Laden der Seite](assets/pageload.png)

1. Ein Aufruf gibt Experience Cloud ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem weiteren Aufruf die Kunden-ID synchronisiert.

1. `at.js` -Bibliothek wird synchron geladen und blendet den Dokumentkörper aus (`at.js` kann auch asynchron mit einem optionalen Pre-hiding-Snippet geladen werden, das auf der Seite implementiert ist).

1. Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profilskripte werden ausgeführt und in die [!UICONTROL Profile Store] eingespeist. Der Store ruft geeignete Zielgruppen von [!UICONTROL Audience Library] ab (z. B. über [!DNL Analytics] freigegebene Zielgruppen, Audience Manager usw.). [!UICONTROL Customer Attributes] wird in einem Batch-Prozess an [!UICONTROL Profile Store] gesendet.
1. Basierend auf URL, Anforderungsparametern und Profildaten entscheidet [!DNL Target], welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden sollen

1. Zielgerichteter Inhalt, der zurück an die Seite gesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.

   Zielgerichteter Inhalt auf der aktuellen Seite wird so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.

   Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Siehe nächstes Diagramm für das Verhalten `triggerView()` ).

1. [!DNL Analytics] Daten, die von der Seite an die [!UICONTROL Data Collection]-Server gesendet werden
1. [!DNL Target] -Daten werden über die SDID mit Analytics-Daten abgeglichen und im [!DNL Analytics] -Berichtspeicher verarbeitet. [!DNL Analytics] -Daten können dann sowohl in [!DNL Analytics] als auch in [!DNL Target] über A4T-Berichte angezeigt werden.

![Verhalten von at.js 2.0 bei Verwendung der Funktion triggerView()](assets/triggerview.png)

1. `adobe.target.triggerView()` wird in der Einzelseitenanwendung aufgerufen
1. Zielgerichteter Inhalt für die Ansicht wird aus dem Cache gelesen

1. Zielgerichtete Inhalte werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte flackern

1. Die Benachrichtigungsanfrage wird an [!DNL Target] [!UICONTROL Profile Store] gesendet, um den Besucher in der Aktivität zu zählen und die Metriken zu erhöhen.
1. [!DNL Analytics] Daten werden vom SPA an die [!UICONTROL Data Collection] Server gesendet

1. [!DNL Target] -Daten werden vom [!DNL Target] -Backend an die [!UICONTROL Data Collection] -Server gesendet. [!DNL Target] -Daten werden über die SDID mit [!DNL Analytics] -Daten abgeglichen und in den [!DNL Analytics] -Berichtspeicher verarbeitet. [!DNL Analytics] -Daten können dann sowohl in [!DNL Analytics] als auch in [!DNL Target] über A4T-Berichte angezeigt werden.

## Zusätzliche Ressourcen

* [Implementieren von at.js 2.0 in eine Einzelseiten-App](implement-atjs-20-in-a-single-page-application.md)
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseiten-Apps (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
