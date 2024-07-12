---
title: Optimieren der Adobe Target-Implementierung
description: Verschaffen Sie sich einen Überblick über die Implementierung und Struktur von Adobe Target. Erfahren Sie, wie Sie die Einrichtung Ihres Unternehmens verstehen und überprüfen können. Erfahren Sie mehr über die gängigen Verfahren zur Fehlerbehebung und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team.
solution: Target
feature: Overview
role: Leader, User
exl-id: 49b69f41-0993-437c-bb69-84392be427df
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1129'
ht-degree: 0%

---

# Optimieren der Adobe Target-Implementierung

Wenn Sie mit Ihrer Organisation noch nicht vertraut sind und sich mit den vorhandenen Funktionen aus einer Test- und Optimierungspraxis vertraut machen möchten, hilft Ihnen dieser Artikel bei den ersten Schritten. Zunächst erhalten Sie einen Überblick über die Implementierung und Struktur von Adobe Target. Sie erfahren, wie Sie die Einrichtung Ihres Unternehmens verstehen und überprüfen können. Schließlich besprechen wir gängige Fehlerbehebungsverfahren und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team.

Adobe Target ist ein Tool, mit dem individuelle Inhalte für verschiedene Besucher getestet und zielgerichtet eingesetzt werden können. Eine Übersicht über die verfügbaren Funktionen finden Sie in [diesem Handbuch](https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en).

## Target-Implementierung und -Struktur

Bevor wir uns mit dem Implementierungsprozess für Adobe Target oder dessen Struktur befassen, ist es hilfreich, zunächst einige Grundlagen über die Software zu verstehen.

Adobe Target ist ein Tool, mit dem individuelle Inhalte für verschiedene Besucher getestet und zielgerichtet eingesetzt werden können, ohne den nativen Website-Code zu ändern. Target ändert vorübergehend das Endbenutzererlebnis und verfolgt das Verhalten der Benutzer nach der Änderung. Target bietet außerdem die Möglichkeit, das Erlebnis für Endbenutzer basierend auf Profilinformationen oder vorherigen Aktionen zu ändern.

Es gibt drei grundlegende Aktivitätstypen von Target:

1. A/B-Test
2. Multivarianz-Tests (MVT)
3. Erlebnistests

**Der A/B-Test** vergleicht zwei oder mehr Erlebnisse, um festzustellen, durch welche Erlebnisse die Konversionen über einen vorab festgelegten Testzeitraum am besten verbessert werden. Der A/B-Test ist ein stark kontrolliertes Experiment mit Traffic-Messungen, die nach Prozentsätzen und nicht nach einer Regel aufgeteilt sind, sodass Sie:

* um die Testdaten zu analysieren.
* um Einblicke in Ihre Audience zu erhalten.
* , um zu bestimmen, welches Erlebnis die beste Leistung erzielt.

**Multivarianz-Tests** (MVT) vergleicht Angebotskombinationen zwischen Elementen auf einer Seite, um zu sehen, welche Kombination für eine bestimmte Zielgruppe die beste Leistung erzielt. Dieser Test ermittelt auch, welches Element der Seite die Konversionen während eines zuvor festgelegten Testzeitraums am besten verbessert. MVT bietet:

* Eine Möglichkeit, mehrere Angebote in mehreren Elementen anzuzeigen.
* Eine Methode zum Testen des resultierenden eindeutigen Erlebnisses mit einem bestimmten Ziel.
* Einblicke, welche Elemente die größten negativen oder positiven Auswirkungen auf die Besucherinteraktionen haben.

**Erlebnistests** (Erlebnis-Targeting) stellen Inhalte für eine bestimmte Zielgruppe basierend auf einem Satz von Regeln und Kriterien bereit, die von Marketingexperten definiert wurden. Diese Methode bietet eine Möglichkeit, bestimmte Inhalte basierend auf definierten Zuordnungsregeln auf eine bestimmte Zielgruppe auszurichten.

Wie funktioniert Target?

Hier finden Sie ein Beispiel für die Funktionsweise von Target:

1. Ein Besucher fordert eine Seite von Ihrem Server an und sie wird im Browser angezeigt.
1. Im Browser des Besuchers wird ein Erstanbieter-Cookie gesetzt, um das Verhalten zu speichern.
1. Die Seite ruft dann Adobe Target auf.
1. Der Inhalt wird basierend auf den Regeln der Benutzeraktivität angezeigt.
1. Adobe Target erfasst spezifische Metriken, wie in der Aktivitätskonfiguration definiert, um die Auswirkungen der Testerlebnisse zu messen.

Target basiert auf einer &quot;globalen Mbox&quot;, die die Möglichkeit bietet, alles auf der Seite zu beeinflussen. Diese Funktion wird beim Laden der Seite entweder als hartcodierter Link zur Datei at.js bereitgestellt oder über einen Tag-Manager wie Adobe Launch bereitgestellt.

## Aktuelle Implementierung verstehen

Um Ihre aktuelle Implementierung zu verstehen, empfiehlt Adobe, dass Sie Ihre Target-Benutzeroberfläche zusammen mit Ihrer Tag-Manager- und Seitenlade-Implementierung überprüfen.

**Überprüfen der [!DNL Target]-Benutzeroberfläche:**

1. Beginnen Sie Ihre Überprüfung auf der [!DNL Target] -Benutzeroberfläche:

   * Überprüfen Sie den [!DNL Target]-Technologie-Stack.
   * Verfügbare Funktionen bestätigen
   * Identifizieren, wo die Bereitstellung live ist

1. Überprüfen Sie Aktivitäten auf Best Practices:

   * Überprüfung historischer Kampagnen zur Programmreife

1. Deaktivieren Sie alte Aktivitäten:

   * [!DNL Target]-Asset archivieren und bereinigen, das nicht mehr aktuell oder künftig verwendet wird

1. Zielgruppen überprüfen.

1. Überprüfen Sie die Umgebungsdefinitionen und die zugehörigen Domänen.

1. Überprüfen von Profilskripten auf Anwendbarkeit

   * Alle Profilskripte werden bei jedem Zielaufruf ausgeführt
   * Aufrechterhaltung der Anrufeffizienz durch Entfernen nicht zutreffender Skripte

Überprüfen des Tag-Managers und des Seitenladevorgangs:

1. Bestätigen Sie Folgendes im Tag-Manager:

   * Die Bereitstellung des erwarteten [!DNL Target] JavaScript-Codes
   * Die geeignete Lösung zum Ausblenden von Inhalten
   * Legen Sie die erforderlichen Regeln fest, um die [!DNL Target] -Aufrufe mit den erwarteten Parametern zu füllen.

1. Bestätigen Sie beim Laden der Seite Folgendes:

   * Abgleichen von Versionsnummern für die Anfrage-URL und [!DNL Target] Anfrage-URL
   * Befüllter Experience Cloud ID-Wert (Cloud Body)
   * Vorgestellte erwartete Integrationswerte (Cloud-Body)
   * Befüllte Parameter [!DNL Target] auf den entsprechenden Seiten

## [!DNL Target] Audit-Aktivitäten

Um zu vermeiden, dass die einzelnen Seiten zur Prüfung von [!DNL Target] -Aktivitäten manuell durchlaufen werden, verwenden Sie Adobe Auditor , um den aktuellen technischen Status Ihrer Implementierung besser zu verstehen. Adobe Auditor wird von ObservePoint unterstützt und kann für die Ausführung auf manueller Ebene eingerichtet werden, um Probleme bei der Implementierung auf hoher Ebene auf Ihrer Site zu identifizieren.

Der Adobe Auditor bietet Folgendes:

* Hohe Site-Gesundheit
* Kurzanfragen zu Implementierungsproblemen

Adobe empfiehlt, monatliche manuelle Audits durchzuführen, um

* Identifizieren von Seiten ohne Tags
* Inkonsistente Versionen identifizieren
* Ermitteln von veralteten Versionen
* Detaillierte Informationen bereitstellen, die exportiert werden können

## Allgemeine Fehlerbehebung

>[!NOTE]
>
>Adobe empfiehlt die Installation des Adobe Experience Platform Debuggers.

Im Folgenden finden Sie allgemeine Tipps zur Fehlerbehebung bei der Eingabe des Erlebnisses:

### Cache und Cookies**

* Löschen von Cache und Cookies
* Gehen Sie beim privaten Modus vorsichtig vor (z. B.: Der private Modus in Firefox kann [!DNL Target] blockieren.

### Sind Sie für die Aktivität qualifiziert?

* Vergewissern Sie sich, dass Sie dieselben Schritte ausgeführt haben wie die in der Aktivität verwendete Zielgruppe.
* Verwenden Sie `mboxTrace` oder Antwort-Token, um Profil- und Segmentwerte zu überprüfen.

### Allgemeine Tipps zur Fehlerbehebung bei der Validierung von visuellen/funktionalen

Wenn Sie sich im Erlebnis [!DNL Target] befinden und das erwartete visuelle Erlebnis nicht angezeigt wird:

Überprüfen Sie die Antwort [!DNL Target] :

* Wenn der Code nicht ausgeführt wird:

1. Überprüfen von in Konflikt stehenden Aktivitäten
1. Kundenunterstützung kontaktieren

* Wenn der Code ausgeführt wird:

1. Bearbeiten Sie den Code in diesem Szenario erneut.

## Wissensspeicher verwalten

Ein Wissens-Repository ist eine Online-Plattform für die Dokumentation und den Austausch von Informationen. Das Wissens-Repository enthält spezifische Informationen zu Ihrer Implementierung und kann Team-spezifische Informationen enthalten.

Idealerweise sollte das Repository die Bearbeitung und automatische Speicherung auf der Plattform zulassen. Nach der anfänglichen Konfiguration ist es einfach zu verwalten und auf dem neuesten Stand zu halten. Inhalte im Wissens-Repository werden basierend auf Benutzerrollen kuratiert.

Zu den typischen Dokumenten in einem Wissens-Repository gehören:

* **Übersichtsdokument** - ein Dokument, das verwendet wird, um Programmziele, -prozesse und -struktur klar zu erklären
* **Ideen-Repository** - ein Dokument zur Verwaltung und Priorisierung potenzieller Ideen, die für den Testprozess noch nicht bereit sind
* **Programm-Roadmap** - ein Dokument, mit dem alle Aspekte von Testaktivitäten verwaltet werden, sobald Ideen bereit sind, den Testprozess zu starten
* **Dokument &quot;Aktivitätsplan&quot;** - ein Dokument, in dem Informationen beschrieben werden, die zum Erstellen und Starten von Aktivitäten erforderlich sind
* **Dokument &quot;Aktivitätsplan&quot;** - ein Dokument, das verwendet wird, um Ergebnisse zu kommunizieren, und empfohlene nächste Schritte an die Stakeholder
* **Programm-Dashboard** - ein Dokument, mit dem die Leistung, Kadenz und Umsatzvorteile des Programms im Zeitverlauf verfolgt werden.

Weitere Informationen finden Sie in unserem [Webinar](https://adobecustomersuccess.adobeconnect.com/p4p7xlp7dh42mp4/) bei Senior Consultant, Wilder Freed.

Erfahren Sie mehr über Strategie und Gedankenführung am [Kundenerfolg](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html)-Hub.
