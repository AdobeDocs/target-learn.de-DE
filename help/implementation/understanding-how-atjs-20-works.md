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
source-wordcount: '412'
ht-degree: 22%

---

# Funktionsweise von Adobe Target at.js 2.0

`at.js` 2.0 verbessert die Unterstützung von Adobe Target für Einzelseitenanwendungen (SPA) und kann mit anderen Experience Cloud-Lösungen integriert werden. In diesem Video und den zugehörigen Diagrammen wird erklärt, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![at.js 2.0-Verhalten beim Laden der Seite](assets/pageload.png)

1. Ein Aufruf gibt die Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem weiteren Aufruf die Kunden-ID synchronisiert.

1. `at.js` Bibliothek wird synchron geladen und blendet den Hauptteil des Dokuments aus (`at.js` kann auch asynchron mit einem optionalen Pre-hiding-Snippet geladen werden, das auf der Seite implementiert ist).

1. Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profilskripte werden ausgeführt und in die [!UICONTROL Profilspeicher]. Der Store fordert geeignete Zielgruppen aus der [!UICONTROL Zielgruppenbibliothek] (z. B. freigegebene Zielgruppen von [!DNL Analytics], Audience Manager usw.). [!UICONTROL Kundenattribute] werden an [!UICONTROL Profilspeicher] in einem Batch-Prozess.
1. Basierend auf URL, Anforderungsparametern und Profildaten, [!DNL Target] bestimmt, welche Aktivitäten und Erlebnisse für die aktuelle Seite und zukünftige Ansichten an den Besucher zurückgegeben werden.

1. Zielgerichteter Inhalt, der zurück an die Seite gesendet wird, optional einschließlich Profilwerten für eine zusätzliche Personalisierung.

   Die zielgerichteten Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.

   Zielgerichtete Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Server-Aufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Siehe nächstes Diagramm für `triggerView()` Verhalten).

1. [!DNL Analytics] Daten, die von der Seite an die [!UICONTROL Datenerfassung] Server
1. [!DNL Target]-Daten werden über die SDID mit -Daten abgeglichen und im [!DNL Analytics]Analytics-Berichtspeicher abgelegt. [!DNL Analytics] -Daten können dann in beiden [!DNL Analytics] und [!DNL Target] über A4T-Berichte.

![Verhalten von at.js 2.0 bei Verwendung der Funktion triggerView()](assets/triggerview.png)

1. `adobe.target.triggerView()` in der Einzelseitenanwendung aufgerufen wird
1. Gezielte Inhalte für die Ansicht werden aus dem Cache gelesen

1. Die zielgerichteten Inhalte werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern

1. Die Benachrichtigungsanfrage wird an den [!DNL Target]-Profilspeicher gesendet, damit der Besucher in der Aktivität erfasst und die Metrik erhöht wird
1. [!DNL Analytics] Daten werden vom SPA an die [!UICONTROL Datenerfassung] Server

1. [!DNL Target] Daten werden von der [!DNL Target] Backend zu [!UICONTROL Datenerfassung] Server. [!DNL Target]-Daten werden über die SDID mit [!DNL Analytics]-Daten abgeglichen und im [!DNL Analytics]-Berichtspeicher abgelegt. [!DNL Analytics] -Daten können dann in beiden [!DNL Analytics] und [!DNL Target] über A4T-Berichte.

## Zusätzliche Ressourcen

* [Implementieren von at.js 2.0 in eine Einzelseiten-App](implement-atjs-20-in-a-single-page-application.md)
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseiten-Apps (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
