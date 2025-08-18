---
title: Optimieren der Adobe Target-Implementierung
description: Verschaffen Sie sich einen Überblick über die Implementierung und Struktur von Adobe Target. Erfahren Sie, wie Sie die Einrichtung Ihres Unternehmens verstehen und prüfen können. Erfahren Sie mehr über gängige Techniken zur Fehlerbehebung und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team.
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

Wenn Sie mit Ihrer Organisation noch nicht vertraut sind und sich mit den vorhandenen Funktionen aus einer Test- und Optimierungspraxis vertraut machen möchten, hilft Ihnen dieser Artikel bei den ersten Schritten. Beginnen wir mit einem Überblick über die Implementierung und Struktur von Adobe Target. Sie erfahren, wie Sie die Einrichtung Ihres Unternehmens verstehen und prüfen können. Schließlich besprechen wir gängige Techniken zur Fehlerbehebung und Tipps zum Erstellen eines Wissens-Repositorys für Ihr Team.

Adobe Target ist ein Tool, mit dem Unique Content getestet und zielgerichtet auf verschiedene Besucher ausgerichtet werden kann. Eine Übersicht über die verfügbaren Funktionen finden [in diesem Handbuch](https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en).

## Target-Implementierung und -Struktur

Bevor wir uns mit dem Implementierungsprozess für Adobe Target befassen oder mit der Struktur, ist es hilfreich, zunächst einige Grundlagen zur Software zu verstehen.

Adobe Target ist ein Tool, mit dem Sie individuelle Inhalte für verschiedene Besucher testen und auswählen können, ohne den nativen Website-Code zu ändern. Target ändert vorübergehend das Erlebnis für Endbenutzer und verfolgt das Verhalten der Benutzer, nachdem sie die Änderung gesehen haben. Target bietet außerdem die Möglichkeit, das Erlebnis für Endbenutzer basierend auf Profilinformationen oder vorherigen Aktionen zu ändern.

Es gibt drei grundlegende Target-Aktivitätstypen:

1. A/B-Test
2. Multivariate Tests (MVT)
3. Erlebnistests

**Der A/B-Test** vergleicht zwei oder mehr Erlebnisse, um festzustellen, welche die Konversionen während eines vorab festgelegten Testzeitraums am besten verbessert. Der A/B-Test ist ein streng kontrolliertes Experiment mit Traffic-Messungen, die nach Prozentsätzen und nicht nach einer Regel aufgeteilt werden. So haben Sie folgende Möglichkeiten:

* , um die Testdaten zu analysieren.
* um Einblicke in Ihre Audience zu erhalten.
* um zu bestimmen, welches Erlebnis die besten Ergebnisse erzielt.

**Multivariate Testing** (MVT) vergleicht Kombinationen von Angeboten zwischen Elementen auf einer Seite, um zu sehen, welche Kombination für eine bestimmte Zielgruppe am besten funktioniert. Dieser Test ermittelt auch, welches Seitenelement die Konversionen während eines vorab festgelegten Testzeitraums am besten verbessert. MVT bietet:

* Eine Möglichkeit, mehrere Angebote in mehreren Elementen anzuzeigen.
* Eine Methode zum Testen des resultierenden eindeutigen Erlebnisses mit einem bestimmten Ziel.
* Insight, welche Elemente die größten negativen oder positiven Auswirkungen auf Besucherinteraktionen haben.

**Erlebnistests** (Erlebnis-Targeting) stellen Inhalte für eine bestimmte Zielgruppe basierend auf einem Satz aus Regeln und Kriterien bereit, die von den Werbungtreibenden definiert werden. Diese Methode bietet die Möglichkeit, bestimmte Inhalte basierend auf einem Satz definierter Zuordnungsregeln auf eine bestimmte Zielgruppe auszurichten.

Wie funktioniert Target?

Im Folgenden finden Sie ein Beispiel auf hoher Ebene für die Funktionsweise von Target:

1. Ein Besucher fordert eine Seite von Ihrem Server an, die im Browser angezeigt wird.
1. Im Browser des Besuchers wird ein Erstanbieter-Cookie gesetzt, um das Verhalten zu speichern.
1. Die Seite ruft dann Adobe Target auf.
1. Der Inhalt wird basierend auf den Regeln der Aktivität des Benutzers angezeigt.
1. Adobe Target erfasst bestimmte Metriken, wie sie in der Aktivitätskonfiguration definiert sind, um die Auswirkungen der Testerlebnisse zu messen.

Target basiert auf einer „globalen Mbox“, die es ermöglicht, alle Aspekte der Seite zu beeinflussen. Diese Funktion wird beim Laden der Seite entweder als hartcodierter Link zur at.js-Datei bereitgestellt oder über einen Tag-Manager wie Adobe Launch bereitgestellt.

## Aktuelle Implementierung verstehen

Um Ihre aktuelle Implementierung zu verstehen, empfiehlt Adobe, die Implementierung Ihrer Target-Benutzeroberfläche zusammen mit Ihrer Tag-Manager- und Seitenladeimplementierung zu überprüfen.

**So überprüfen Sie Ihre [!DNL Target] Benutzeroberfläche:**

1. Beginnen Sie Ihren Review auf der [!DNL Target] Benutzeroberfläche:

   * Überprüfen des [!DNL Target] Technologie-Stacks
   * Bestätigen der verfügbaren Funktionen
   * Ermitteln, wo die Bereitstellung live ist

1. Überprüfen Sie die Aktivitäten auf Best Practices:

   * Überprüfen historischer Kampagnen auf die Programmreife

1. Alte Aktivitäten deaktivieren:

   * Archivieren und bereinigen Sie [!DNL Target] Asset, das nicht mehr aktuell oder zukünftig verwendet wird

1. Überprüfen von Zielgruppen.

1. Überprüfen Sie die Umgebungsdefinitionen und die zugehörigen Domains.

1. Profilskripte auf Anwendbarkeit überprüfen

   * Alle Profilskripte werden bei jedem Target-Aufruf ausgeführt
   * Aufrechterhaltung der Anrufeffizienz durch Entfernen nicht anwendbarer Skripte

So überprüfen Sie den Tag-Manager und das Laden der Seite:

1. Bestätigen Sie Folgendes im Tag-Manager:

   * Die Bereitstellung des erwarteten [!DNL Target] JavaScript-Codes
   * Die geeignete Lösung zum Ausblenden von Inhalten
   * Legen Sie die erforderlichen Regeln fest, um die [!DNL Target]-Aufrufe mit den erwarteten Parametern zu füllen

1. Bestätigen Sie Folgendes beim Laden der Seite:

   * Übereinstimmende Versionsnummern für die Anfrage-URL und [!DNL Target] Anfrage-URL
   * Ausgefüllter Experience Cloud-ID-Wert (Cloud-Hauptteil)
   * Präsentation der erwarteten Integrationswerte (Cloud-Hauptteil)
   * Ausgefüllte [!DNL Target] auf den entsprechenden Seiten

## [!DNL Target] Audittätigkeiten

Um zu vermeiden, dass Sie [!DNL Target] Aktivitäten manuell auf jeder Seite überprüfen müssen, sollten Sie den Adobe Auditor verwenden, um sich über den aktuellen technischen Status Ihrer Implementierung zu informieren. Adobe Auditor basiert auf ObservePoint und kann für die Ausführung auf manueller Ebene eingerichtet werden, um allgemeine Implementierungsprobleme auf Ihrer Site zu identifizieren.

Der Adobe Auditor bietet:

* Hohe Site-Konsistenz
* Schnelle Aufrufe für Implementierungsprobleme

Adobe empfiehlt, monatliche manuelle Audits durchzuführen, um:

* Identifizieren nicht getaggter Seiten
* Identifizieren inkonsistenter Versionen
* Ermitteln veralteter Versionen
* Angeben detaillierter Informationen, die exportiert werden können

## Häufige Fehlerbehebung

>[!NOTE]
>
>Adobe empfiehlt, Adobe Experience Platform Debugger zu installieren.

Im Folgenden finden Sie allgemeine Tipps zur Fehlerbehebung beim Eintritt in das Erlebnis:

### Cache und Cookies**

* Löschen von Cache und Cookies
* Achten Sie auf die Verwendung des privaten Modus (z. B. kann der private Modus in Firefox [!DNL Target] blockieren)

### Sind Sie für die Aktivität qualifiziert?

* Vergewissern Sie sich, dass Sie die gleichen Schritte ausgeführt haben wie die in der Aktivität verwendete Zielgruppe
* Verwenden von `mboxTrace`- oder Antwort-Token zur Überprüfung von Profil- und Segmentwerten

### Allgemeine Tipps zur Fehlerbehebung bei der Validierung von visuellen/funktionellen

Wenn Sie sich im [!DNL Target] befinden und das erwartete visuelle Erlebnis nicht angezeigt wird:

Überprüfen Sie die [!DNL Target] Antwort:

* Wenn der Code nicht ausgeführt wird:

1. Überprüfen von konfliktträchtigen Aktivitäten
1. Kundenunterstützung kontaktieren

* Wenn der Code ausgeführt wird:

1. Code in diesem Szenario überarbeiten

## Verwalten eines Wissens-Repositorys

Ein Wissens-Repository ist eine Online-Plattform für die Dokumentation und den Austausch von Informationen. Das Wissens-Repository enthält spezifische Informationen für Ihre Implementierung und kann teamspezifische Informationen enthalten.

Idealerweise sollte das Repository die Bearbeitung und das automatische Speichern innerhalb der Plattform ermöglichen. Nach der Erstkonfiguration ist es einfach zu pflegen und auf dem neuesten Stand zu halten. Inhalte im Wissens-Repository werden basierend auf Benutzerrollen kuratiert.

Zu den typischen Dokumenten in einem Knowledge Repository gehören:

* **Übersichtsdokument** - Ein Dokument, in dem Programmziele, -ziele, -prozesse und -strukturen klar erläutert werden
* **Ideations-Repository** - ein Dokument, das zur Verwaltung und Priorisierung potenzieller Ideen verwendet wird, die für den Testprozess nicht bereit sind
* **Programm-Roadmap** - Ein Dokument, mit dem alle Aspekte von Testaktivitäten verwaltet werden, sobald die Ideen für den Testprozess bereit sind
* **Aktivitätsplandokument** Ein Dokument, in dem die für die Erstellung und Ausführung von Aktivitäten erforderlichen Informationen beschrieben werden
* **Aktivitätsplandokument** Ein Dokument, das verwendet wird, um den Beteiligten die Ergebnisse und empfohlenen nächsten Schritte mitzuteilen
* **Programm-Dashboard** - Ein Dokument, mit dem die Programmleistung, die Kadenz und der Umsatz im Zeitverlauf verfolgt werden.

Weitere Informationen finden Sie in unserem [Webinar](https://adobecustomersuccess.adobeconnect.com/p4p7xlp7dh42mp4/) mit Senior Consultant, Wilder Freed.

Erfahren Sie mehr über Strategie und Meinungsführerschaft auf dem [Customer Success](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html)-Hub.
