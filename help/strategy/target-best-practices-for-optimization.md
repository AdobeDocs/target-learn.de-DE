---
title: Best Practices für die Optimierung
description: Lernen Sie die sechs Grundlagen der Optimierung von Adobe kennen und erfahren Sie, wie Sie sie anwenden können.
solution: Target
role: Leader, Developer, Admin
feature: Overview
level: Beginner
exl-id: dd29faea-bb67-4128-b261-fa407ba7158c
TQID: https://experienceleague.adobe.com/4M13hg8c1kxAmsBaiSfyvV3XEXLxV5lHEy299YGBvII
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2:
  - id: adee20bd-51f4-461d-b9db-d215f8756eeb
  - id: c93393a4-e558-47e1-992e-c91ed4d480ce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: c7d04a2c-412a-4c9d-9d7a-4456eaa5adeb
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
  - id: f8667931-f646-4dd3-af2a-b9d0cb8098ad
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 1254
ht-degree: 0%

---

# Best Practices für die Optimierung mit Adobe Target

Lernen Sie die sechs Grundlagen der Optimierung von Adobe kennen und erfahren Sie, wie Sie sie anwenden können.

Wenn es darum geht, eine starke digitale Präsenz aufzubauen, gibt es eine Reihe von Herausforderungen, vor denen Ihr Team stehen wird. Sie haben nicht nur die Aufgabe, Hunderte oder sogar Tausende von Kunden zu ansprechen. Darüber hinaus zeigen Ihre Kunden eine Vielzahl einzigartiger Verhaltensweisen und Vorlieben, die sich im Laufe der Zeit ändern werden, und es liegt an Ihnen, nicht nur mit diesen Änderungen Schritt zu halten, sondern sie zu antizipieren und Ihre Strategien effizient und genau auszuführen. Es ist ein Rennen gegen die Konkurrenten in einem permanenten Inhalts-Marathon, der ständige Iteration und erstklassige Technologie erfordert.

Eine Lösung für diese vielseitige Herausforderung ist die Optimierung mit Adobe Target, die sicherstellt, dass Sie über eine sich entwickelnde digitale Präsenz verfügen, die relevant, wertvoll und reibungsfrei ist. Die technische Architektur und die Kanäle, in denen Sie [!DNL Target] bereitstellen, sind von Kunde zu Kunde sehr unterschiedlich. Wir haben jedoch eine Liste mit Best Practices und Optimierungsstrategien zusammengestellt, die jedes Team verwenden kann, um die Möglichkeiten dieses leistungsstarken Tools optimal zu nutzen.

## Grundlegendes zur Optimierung

Optimierung ist definiert als „die Aktion, eine Situation oder Ressource optimal oder am effektivsten zu nutzen.“ Dies ist der effizienteste Weg, um sicherzustellen, dass Sie über qualitative Daten verfügen, die beweisen, dass die von Ihnen vorgenommenen Änderungen nützlich sind. Um wirklich zu optimieren, müssen Sie in der Lage sein, die Wirkung und den Wert Ihrer Bemühungen zu messen. Andernfalls führen die von Ihnen vorgenommenen Änderungen zu höheren Kosten bei minimalem Gewinn. Um dies effektiv und effizient zu erreichen, müssen Sie mit der strategischen Planung beginnen. Ohne einen strategischen Plan in Ihre Optimierung einzubeziehen, würden Sie einfach raten.

### Sechs Grundlagen der Optimierung

1. **Strategie**: Identifizieren Sie Möglichkeiten für Aktivitäten, die mit Geschäftszielen abgestimmt sind und auf Daten basieren.
1. **Priorisieren**: Bewerten und planen Sie die Aktivitäten nach ihrer Ausrichtung am Unternehmen, dem Aufwand und der potenziellen Wirkung.
1. **Design**: Erstellen Sie fertige Visualisierungen der Aktivitätserlebnisse und entwickeln Sie Aktivitätspläne mit detaillierten Kriterien.
1. **Erstellen und Ausführen**: Entwickeln Sie Aktivitäten einschließlich [!DNL Target] Einrichtung, Code-Entwicklung und QA-Tests.
1. **Analysieren**: Starten [!DNL Target] Aktivität für die Produktion und Überwachen der Leistung für die Dauer der Aktivität.
1. **Handeln und iterieren**: Entwickeln Sie Empfehlungen auf der Grundlage der Leistung von Test- oder Personalisierungsaktivitäten.

Da der Wandel eine Konstante ist, sollte unsere Optimierungsstrategie ein iterativer Ausführungszyklus sein, um den sich ständig ändernden Anforderungen Ihrer Kunden gerecht zu werden (siehe Abbildung 1 unten).

![Optimierung und Personalisierung](assets/optimize-and-personalize.png)

_Abbildung 1: Iterativer Optimierungszyklus_

## Erstellen einer Optimierungsstrategie

Der Prozess der Entwicklung einer Optimierungsstrategie kann wie folgt aufgeschlüsselt werden: (1) Erstellen eines Aktivitätsplans für Tests und (2) Grundlagen der Optimierung.

1: Der Aktivitätsplan für den Test sollte dokumentiert werden. Dadurch wird sichergestellt, dass Sie bei Ihrer Testaktivitätsanwendung über einen minimalen Qualitätsstandard verfügen. Ihr Testaktivitätsplan sollte Folgendes enthalten:

* **Name und Beschreibung:** Name der intuitiven Aktivität und Beschreibung dessen, worauf sich das Experiment konzentriert. „Wie? Was? Wann? Wo? Warum?“

* **Ziel** Zweck der Aktivität und abgestimmtes Geschäftsziel, auf deren Wirkung sie ausgelegt ist.

* **Hypothese:** Eine Hypothese ist eine Prognose, die Sie vor der Durchführung eines Experiments erstellen. Hier wird klar gesagt, was getestet wird, was man für das Ergebnis hält und warum man das glaubt. Die Durchführung des Experiments bestätigt oder widerlegt Ihre Hypothese.

Eine vollständige Hypothese besteht aus drei Teilen:

* If _variable_
* Then _result_
* Denn _rational_

* **Speicherort** URL, Seitenbereich und Gerätetyp.
* **Zielmetrik:** wird der Erfolg gemessen?
* **Sekundäre Metriken:** Weitere wichtige Leistungsindikatoren (KPIs), die ausgewertet werden können, um Auswirkungen besser zu verstehen und Iterationen zu planen.
* **Aktivitätszielgruppe:** Beschreibung der erforderlichen Filterung der Testbelichtung.
* **Reporting-Zielgruppen:** Liste der Beschreibungen von Besucheruntergruppen, die für die Analyse verwendet werden sollen.
* **Erlebniskonzepte:** Mockups, Beispiele für Wireframes und Beschreibungen.

**Allgemeiner Hinweis:** Jedes Element einer Web-Seite, das den Geschäftswert steigern oder wertvolle insight für das Besucherverhalten bieten kann, kann getestet werden. Zu den gebräuchlichen Arten von Testaktivitäten gehören:

* Überschrifttext
* Inhaltstext
* Schaltflächentext
* Seitenlayout
* Fotografie
* Schaltflächenfarbe
* Element-Layout
* Entfernen und Hinzufügen von Elementen
* Navigationsreihenfolge
* Navigationstaxonomie
* Suchhervorhebung

2: Die zweite Phase der Strategie besteht darin, die Grundlagen der Optimierung zu verstehen, was das Verständnis der Testelemente selbst umfasst. Zu den Testelementen der Optimierung gehören:

    a. Elementwert
    
    Dies wird erreicht, indem Sie einen Schritt zurück gehen und fragen, warum ein bestimmtes Element auf Ihrer Site vorhanden ist und ob der Inhalt einem bestimmten Zweck dient? Diese Fragen sind ein guter Ausgangspunkt, wenn Ihre Site gerade ein Redesign abgeschlossen hat oder wenn eine neue Funktion kürzlich eingeführt wurde. Die Taktik, mit der der Elementwert bestimmt wird, wird als Ein-/Ausschlusstest bezeichnet. Ein-/Ausschlusstests bieten eine gute Wertschätzung auf der Seite, auf der das Element angezeigt wird.
    
    B. Elementdarstellung
    
     Hier würden Sie über das Gesamtbild des Elements und dessen Auswirkungen auf die gesamte Seitendarstellung nachdenken. Die Taktik, die für die Präsentation verwendet wird, besteht darin, sich auf wirkungsvolle Inhalts- und Seitenelementänderungen zu konzentrieren
    
    C. Elementfunktion
    
    Hier fragen wir, ob das Element auf der Seite das tut, was es tun soll? Funktioniert die Interaktion erfolgreich und wie beabsichtigt? Ist die Interaktion natürlich oder ein Reibungspunkt? Die für Funktionen verwendete Taktik besteht darin, Erlebnisse zu erstellen, die sich auf benutzerfreundliche Funktionen ohne zusätzliche Kostenauswirkungen konzentrieren.

## Optimierung vs. Personalisierung

Nachdem wir nun die Komponenten der Strategie analysiert und aufgelistet haben, ist es wichtig, zwischen Optimierungsbemühungen und Personalization-Maßnahmen zu unterscheiden. Optimierung ist die Maßnahme, eine Situation oder Ressource am besten oder effektivsten zu nutzen, während Personalization die Maßnahme ist, etwas zu entwerfen oder zu produzieren, das den individuellen Anforderungen einer Person entspricht.

Auf allgemeiner Ebene:

* Die Optimierung konzentriert sich auf Tests, um herauszufinden, was für ALLE am effizientesten und leistungsfähigsten ist, die mit Ihrer digitalen Präsenz interagieren.
* Personalization testet, was für einige von denen, die mit Ihrer digitalen Präsenz interagieren, am effizientesten und leistungsfähigsten ist.

Wenn wir uns auf die Optimierung konzentrieren, sind die häufigsten Testaktivitäten:

* **A/B-Tests** Echtzeit-Tests von zwei oder mehr Seiten oder Seitenelementen gegeneinander, um quantitative insight in die Kundenpräferenz zu bringen.
* **Multivariate Tests** Vergleichen von Angebotskombinationen zwischen Elementen auf einer Seite, um festzustellen, welche Kombination die besten Ergebnisse erzielt. Darüber hinaus ermittelt der Multivarianz-Test, welches Element der Seite die Konversionen am besten verbessert.

Wenn Sie sich auf Personalization konzentrieren, sehen Sie wahrscheinlich dieselben Testaktivitäten wie in Optimierung, sie sind jedoch auf spezifischere Zielgruppen ausgerichtet. Bei A/B-Tests werden Sie beispielsweise wahrscheinlich Seiten und Zielgruppen innerhalb der Erlebnisse hinzufügen, um Ihre Personalization weiter zu unterstützen.

Personalization umfasst auch den Testaktivitätstyp Experience Targeting , der basierend auf einem Satz definierter Regeln und Kriterien Inhalte für bestimmte Zielgruppen bereitstellt. Wenn Sie mit dem Wachstum und der Vertiefung in Personalization beginnen, werden Sie auch einige der Premium-Funktionen von Target nutzen, wie:

* Automated Personalization-Aktivitätstyp
* Recommendations-Aktivitätstyp

## Optimierung vor Personalisierung

Angesichts der oben genannten Informationen empfiehlt Adobe, vor der Personalisierung zu optimieren und Personalization von einer umfassenden zu einer granularen Lösung zu entwickeln. Um Personalization-Aktivitäten von umfangreich bis detailliert zu entwickeln, verwenden Sie zunächst einen universellen Personalisierungsstil (breiter Stil) (mithilfe von A/B-Tests) und wechseln dann zum granularen Einzelpersonalisierungsstil (mithilfe von Automated Personalization-Aktivitäten).

Weitere Informationen finden Sie im Abschnitt [Schnellstart für Personalisierungstests und Erstellung von Roadmaps](https://experienceleague.adobe.com/de/perspectives/quickstart-for-personalization-testing-and-roadmap-creation).

Erfahren Sie mehr über Strategie und Meinungsführerschaft im [Perspektiven](https://experienceleague.adobe.com/de/perspectives)-Hub.
