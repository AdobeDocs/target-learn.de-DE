---
title: Funktionsweise von "at.js"in Adobe Target
seo-title: Funktionsweise von "at.js"in Adobe Target
description: '"at.js 2.0"erweitert die Unterstützung von Adobe Targets für Einzelseitenanwendungen (SPA) und ermöglicht die Integration in andere Experience Cloud-Lösungen. Dieses Video und die zugehörigen Diagramme erklären, wie alles zusammenkommt.'
audience: developer
difficulty: 3
author: Daniel Wright
doc-type: implement
activity-type: technical-video
translation-type: tm+mt
source-git-commit: 37443ae4c1cdda387c8db0053201d520fa1ec224
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 20%

---


# Funktionsweise von &quot;at.js&quot;in Adobe Target

`at.js` 2.0 verbessert die Unterstützung von Adobe Targets für Einzelseitenanwendungen (SPA) und integriert sich in andere Experience Cloud-Lösungen. Dieses Video und die zugehörigen Diagramme erklären, wie alles zusammenkommt.

>[!VIDEO](https://video.tv.adobe.com/v/26250?quality=12)

## Architekturdiagramme

![at.js 2.0-Verhalten beim Laden der Seite](assets/pageload.png)

1. Aufruf gibt Experience Cloud-ID (ECID) zurück. Wenn der Benutzer authentifiziert ist, wird bei einem anderen Aufruf die Kunden-ID synchronisiert.

1. `at.js` Bibliothek wird synchron geladen und blendet den Textkörper des Dokuments aus (`at.js` kann auch asynchron mit einem optionalen, auf der Seite implementierten Präausblendeffekt geladen werden).

1. Die Seitenladeanforderung umfasst alle konfigurierten Parameter, ECID, SDID und Kunden-ID.

1. Profile scripts execute and feed into the [!UICONTROL Profile Store]. The Store requests qualified audiences from the [!UICONTROL Audience Library] (e.g. audiences shared from [!DNL Analytics], Audience Manager, etc). [!UICONTROL Kundenattribute] werden in einem Stapelprozess an den [!UICONTROL Profil Store] gesendet.
1. Based on URL, request parameters, and profile data, [!DNL Target] decides which Activities and Experiences to return to the visitor for the current page and future views

1. Targeting von Inhalten, die an die Seite zurückgesendet werden, einschließlich optional Profil-Werten für eine zusätzliche Personalisierung.

   Die zielgerichteten Inhalte auf der aktuellen Seite werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern.

   Gezielte Inhalte für zukünftige Ansichten einer Einzelseitenanwendung werden im Browser zwischengespeichert, sodass sie sofort ohne zusätzlichen Serveraufruf angewendet werden können, wenn die Ansichten ausgelöst werden. (Siehe nächstes Diagramm für `triggerView()` Verhalten).

1. [!DNL Analytics] Daten, die von der Seite an die [!UICONTROL Datenerfassungsserver] gesendet werden
1. [!DNL Target]-Daten werden über die SDID mit -Daten abgeglichen und im [!DNL Analytics]Analytics-Berichtspeicher abgelegt. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

![Verhalten von at.js 2.0 bei Verwendung der Funktion &quot;triggerView()&quot;](assets/triggerview.png)

1. `adobe.target.triggerView()` in der einseitigen Anwendung aufgerufen wird
1. Gezielte Inhalte für die Ansicht werden aus dem Cache gelesen

1. Die zielgerichteten Inhalte werden so schnell wie möglich bereitgestellt, ohne dass Standardinhalte aufflackern

1. Die Benachrichtigungsanfrage wird an den [!DNL Target]-Profilspeicher gesendet, damit der Besucher in der Aktivität erfasst und die Metrik erhöht wird
1. [!DNL Analytics] Daten werden von der SPA an die [!UICONTROL Datenerfassungsserver] gesendet

1. [!DNL Target] Daten werden vom [!DNL Target] Backend an die [!UICONTROL Datenerfassungsserver] gesendet. [!DNL Target]-Daten werden über die SDID mit [!DNL Analytics]-Daten abgeglichen und im [!DNL Analytics]-Berichtspeicher abgelegt. [!DNL Analytics] Daten können dann sowohl in [!DNL Analytics] als auch [!DNL Target] über A4T-Berichte angezeigt werden.

## Zusätzliche Ressourcen

* [&quot;at.js 2.0&quot;in eine Einzelseitenanwendung implementieren](implement-atjs-20-in-a-single-page-application.md)
* [Visual Experience Composer von Adobe Target für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Funktionsweise von &quot;at.js&quot;](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/at-js/how-atjs-works.html)