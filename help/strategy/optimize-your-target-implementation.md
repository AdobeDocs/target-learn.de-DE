---
title: Optimieren der Adobe Target-Implementierung
description: 'Verschaffen Sie sich einen Überblick über die Implementierung und Struktur von Adobe Target. Erfahren Sie, wie Sie die Einrichtung Ihres Unternehmens verstehen und überprüfen können. Erfahren Sie mehr über die gängigen Verfahren zur Fehlerbehebung und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team. '
solution: Target
source-git-commit: fd679d3fc2c72b9852d8129adf8c1187bf22b25f
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 0%

---

# Optimieren der Adobe Target-Implementierung

Wenn Sie mit Ihrer Organisation noch nicht vertraut sind und sich mit den vorhandenen Funktionen aus einer Test- und Optimierungspraxis vertraut machen möchten, hilft Ihnen dieser Artikel bei den ersten Schritten. Zunächst erhalten Sie einen Überblick über die Implementierung und Struktur von Adobe Target. Sie erfahren, wie Sie die Einrichtung Ihres Unternehmens verstehen und überprüfen können. Schließlich besprechen wir gängige Fehlerbehebungsverfahren und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team.

Adobe Target ist ein Tool, mit dem individuelle Inhalte für verschiedene Besucher getestet und zielgerichtet eingesetzt werden können. Einen Überblick über die verfügbaren Funktionen erhalten Sie unter [Dieses Handbuch besuchen](https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en).

## Target-Implementierung und -Struktur

Bevor wir uns mit dem Implementierungsprozess für Adobe Target oder dessen Struktur befassen, ist es hilfreich, zunächst einige Grundlagen über die Software zu verstehen.

Adobe Target ist ein Tool, mit dem individuelle Inhalte für verschiedene Besucher getestet und zielgerichtet eingesetzt werden können, ohne den nativen Website-Code zu ändern. Target ändert vorübergehend das Endbenutzererlebnis und verfolgt das Verhalten der Benutzer nach der Änderung. Target bietet außerdem die Möglichkeit, das Erlebnis für Endbenutzer basierend auf Profilinformationen oder vorherigen Aktionen zu ändern.

Es gibt drei grundlegende Aktivitätstypen von Target:

1. A/B-Test
2. Multivarianz-Tests (MVT)
3. Erlebnistests

**A/B-Test** Vergleicht zwei oder mehr Erlebnisse, um festzustellen, durch welche Erlebnisse Konversionen über einen vorab festgelegten Testzeitraum am besten verbessert werden. Der A/B-Test ist ein stark kontrolliertes Experiment mit Traffic-Messungen, die nach Prozentsätzen und nicht nach einer Regel aufgeteilt sind, sodass Sie:

* um die Testdaten zu analysieren.
* um Einblicke in Ihre Audience zu erhalten.
* , um zu bestimmen, welches Erlebnis die beste Leistung erzielt.

**Multivarianz-Tests** (MVT) vergleicht Angebotskombinationen zwischen Elementen auf einer Seite, um festzustellen, welche Kombination für eine bestimmte Zielgruppe die beste Leistung erzielt. Dieser Test ermittelt auch, welches Element der Seite die Konversionen während eines zuvor festgelegten Testzeitraums am besten verbessert. MVT bietet:

* Eine Möglichkeit, mehrere Angebote in mehreren Elementen anzuzeigen.
* Eine Methode zum Testen des resultierenden eindeutigen Erlebnisses mit einem bestimmten Ziel.
* Einblicke, welche Elemente die größten negativen oder positiven Auswirkungen auf die Besucherinteraktionen haben.

**Erlebnistests** (Erlebnis-Targeting) stellt Inhalte für eine bestimmte Zielgruppe basierend auf einem Satz von Regeln und Kriterien bereit, die von Marketingexperten definiert wurden. Diese Methode bietet eine Möglichkeit, basierend auf einem Satz definierter Zuordnungsregeln bestimmte Inhalte auf eine bestimmte Zielgruppe auszurichten.

Wie funktioniert Target?

Hier finden Sie ein Beispiel für die Funktionsweise von Target:

1. Ein Besucher fordert eine Seite von Ihrem Server an und sie wird im Browser angezeigt.
1. Im Browser des Besuchers wird ein Erstanbieter-Cookie gesetzt, um das Verhalten zu speichern.
1. Die Seite ruft dann Adobe Target auf.
1. Der Inhalt wird basierend auf den Regeln der Benutzeraktivität angezeigt.
1. Adobe Target erfasst spezifische Metriken, wie in der Aktivitätskonfiguration definiert, um die Auswirkungen der Testerlebnisse zu messen.

Target basiert auf einer &quot;globalen Mbox&quot;, die es ermöglicht, alles auf der Seite zu beeinflussen. Diese Funktion wird beim Laden der Seite entweder als hartcodierter Link zur Datei at.js bereitgestellt oder über einen Tag-Manager wie Adobe Launch bereitgestellt.

## Aktuelle Implementierung verstehen

Um Ihre aktuelle Implementierung zu verstehen, empfiehlt Adobe, dass Sie Ihre Target-Benutzeroberflächenimplementierung zusammen mit Ihrem Tag-Manager und Ihrer Seitenlade-Implementierung überprüfen.

**So überprüfen Sie Ihre [!DNL Target] Benutzeroberfläche:**

1. Beginnen Sie Ihre Überprüfung auf der [!DNL Target] Benutzeroberfläche:

   * Überprüfen Sie die [!DNL Target] Technologiestapel
   * Verfügbare Funktionen bestätigen
   * Identifizieren, wo die Bereitstellung live ist

1. Überprüfen Sie Aktivitäten auf Best Practices:

   * Überprüfung historischer Kampagnen zur Programmreife

1. Deaktivieren Sie alte Aktivitäten:

   * Archivieren und bereinigen [!DNL Target] Asset, das nicht mehr aktuell oder künftig verwendet wird

1. Zielgruppen überprüfen.

1. Überprüfen Sie die Umgebungsdefinitionen und die zugehörigen Domänen.

1. Überprüfen von Profilskripten auf Anwendbarkeit

   * Alle Profilskripte werden bei jedem Zielaufruf ausgeführt
   * Aufrechterhaltung der Anrufeffizienz durch Entfernen nicht zutreffender Skripte

Überprüfen des Tag-Managers und des Seitenladevorgangs:

1. Bestätigen Sie Folgendes im Tag-Manager:

   * Bereitstellung der erwarteten [!DNL Target] JavaScript-Code
   * Die geeignete Lösung zum Ausblenden von Inhalten
   * Legen Sie die erforderlichen Regeln fest, um die [!DNL Target] Aufrufe mit den erwarteten Parametern

1. Bestätigen Sie beim Laden der Seite Folgendes:

   * Abgleichen von Versionsnummern für die Anfrage-URL und [!DNL Target] Anforderungs-URL
   * Befüllter Experience Cloud ID-Wert (Cloud Body)
   * Vorgestellte erwartete Integrationswerte (Cloud Body)
   * Befüllt [!DNL Target] Parameter auf den entsprechenden Seiten

## [!DNL Target] Audittätigkeiten

So vermeiden Sie, dass die einzelnen zu prüfenden Seiten manuell durchlaufen werden [!DNL Target] -Aktivitäten verwenden, verwenden Sie Adobe Auditor , um den aktuellen technischen Stand Ihrer Implementierung zu verstehen. Adobe Auditor wird von ObservePoint unterstützt und kann für die Ausführung auf manueller Ebene eingerichtet werden, um allgemeine Implementierungsprobleme auf Ihrer Site zu identifizieren.

Adobe Auditor bietet:

* Hohe Site-Gesundheit
* Kurzanfragen zu Implementierungsproblemen

Adobe empfiehlt die Durchführung monatlicher manueller Audits für:

* Identifizieren von Seiten ohne Tags
* Inkonsistente Versionen identifizieren
* Ermitteln von veralteten Versionen
* Detaillierte Informationen bereitstellen, die exportiert werden können

## Allgemeine Fehlerbehebung

>[!NOTE]
>
>Adobe empfiehlt die Installation des Adobe Experience Platform Debugger.

Im Folgenden finden Sie allgemeine Tipps zur Fehlerbehebung bei der Eingabe des Erlebnisses:

### Cache und Cookies**

* Löschen von Cache und Cookies
* Gehen Sie beim Verwenden des privaten Modus vorsichtig vor (z. B.: Der private Modus in Firefox kann blockieren [!DNL Target])

### Sind Sie für die Aktivität qualifiziert?

* Vergewissern Sie sich, dass Sie dieselben Schritte ausgeführt haben wie die in der Aktivität verwendete Zielgruppe.
* Verwendung `mboxTrace` oder Antwort-Token zur Überprüfung von Profil- und Segmentwerten

### Allgemeine Tipps zur Fehlerbehebung bei der Validierung von visuellen/funktionalen

Wenn sich im [!DNL Target] -Erlebnis angezeigt und Sie sehen nicht das erwartete visuelle Erlebnis:

Überprüfen Sie die [!DNL Target] Antwort:

* Wenn der Code nicht ausgeführt wird:

1. Überprüfen von in Konflikt stehenden Aktivitäten
1. Kundenunterstützung kontaktieren

* Wenn der Code ausgeführt wird:

1. Bearbeiten Sie den Code in diesem Szenario erneut.

## Wissensspeicher verwalten

Ein Wissens-Repository ist eine Online-Plattform für die Dokumentation und den Austausch von Informationen. Das Wissens-Repository enthält spezifische Informationen zu Ihrer Implementierung und kann Team-spezifische Informationen enthalten.

Idealerweise sollte das Repository die Bearbeitung und automatische Speicherung auf der Plattform zulassen. Nach der anfänglichen Konfiguration ist es einfach zu verwalten und auf dem neuesten Stand zu halten. Inhalte im Wissens-Repository werden basierend auf Benutzerrollen kuratiert.

Zu den typischen Dokumenten in einem Wissens-Repository gehören:

* **Übersichtsdokument** - ein Dokument, in dem die Programmziele, -ziele, -prozesse und -struktur klar erläutert werden;
* **Ideenrepository** - ein Dokument zur Verwaltung und Priorisierung potenzieller Ideen, die noch nicht für den Testprozess bereit sind
* **Programm-Roadmap** - ein Dokument zur Verwaltung aller Aspekte von Testaktivitäten, sobald Ideen bereit sind, den Testprozess zu starten
* **Dokument zum Aktivitätsplan** - ein Dokument, in dem Informationen beschrieben werden, die zum Erstellen und Starten von Aktivitäten benötigt werden
* **Dokument zum Aktivitätsplan** - ein Dokument zur Übermittlung der Ergebnisse und zur Empfehlung der nächsten Schritte an die Interessenträger
* **Programm-Dashboard** - ein Dokument zur Verfolgung der Programmleistung, -cadenz und -einnahmen im Laufe der Zeit.

Weitere Informationen finden Sie in unserer [Webinar](https://adobecustomersuccess.adobeconnect.com/p4p7xlp7dh42mp4/) mit Senior Consultant, Wilder Freed.
