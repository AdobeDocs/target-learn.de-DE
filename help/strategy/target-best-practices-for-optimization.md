---
title: Best Practices für die Optimierung
description: Erfahren Sie mehr über Adobe und sechs wesentliche Aspekte der Anwendung.
solution: Target
role: Leader, Architect, Developer, Admin
feature: Overview
level: Beginner
exl-id: dd29faea-bb67-4128-b261-fa407ba7158c
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1244'
ht-degree: 0%

---

# Best Practices für die Optimierung mit Adobe Target

Erfahren Sie mehr über Adobe und sechs wesentliche Aspekte der Anwendung.

Wenn es darum geht, eine starke digitale Präsenz aufzubauen, wird Ihr Team vor einer Reihe von Herausforderungen stehen. Sie sind nicht nur dafür verantwortlich, Hunderte, sogar Tausende von Kunden zu beschäftigen, sondern auch dafür, dass Ihre Kunden eine Vielzahl einzigartiger Verhaltensweisen und Präferenzen zeigen, die sich im Laufe der Zeit ändern werden. Es liegt an Ihnen, nicht nur mit diesen Änderungen Schritt zu halten, sondern sie auch vorherzusehen und Ihre Strategien effizient und präzise auszuführen. Es ist ein Wettlauf gegen Konkurrenten in einem ewigen Inhaltsmarathon, der ständige Iteration und erstklassige Technologie erfordert.

Eine Lösung für diese vielschichtige Herausforderung ist die Optimierung mit Adobe Target, die sicherstellt, dass Sie eine sich entwickelnde digitale Präsenz haben, die relevant, wertvoll und reibungslos ist. Die technische Architektur und die Kanäle, in denen Sie [!DNL Target] bereitstellen, variieren von Kunde zu Kunde erheblich. Wir haben jedoch eine Liste mit Best Practices und Optimierungsstrategien erstellt, die jedes Team verwenden kann, um die gesamten Funktionen dieses leistungsstarken Tools nutzen zu können.

## Erläuterungen zur Optimierung

Optimierung wird definiert als &quot;die Aktion, eine Situation oder Ressource optimal oder optimal zu nutzen&quot;. Dies ist der effizienteste Weg, um sicherzustellen, dass Sie über qualitative Daten verfügen, die belegen, dass die von Ihnen vorgenommenen Änderungen nützlich sind. Um Ihre Bemühungen wirklich zu optimieren, müssen Sie in der Lage sein, die Wirkung und den Wert Ihrer Bemühungen zu messen. Andernfalls führen die von Ihnen vorgenommenen Änderungen zu höheren Kosten und minimalem Gewinn. Um dies effektiv und effizient zu erreichen, müssen Sie mit der strategischen Planung beginnen. Ohne einen strategischen Plan in Ihre Optimierung zu integrieren, würden Sie einfach raten.

### Sechs wesentliche Optimierungsschritte

1. **Strategien**: Ermitteln Sie Möglichkeiten für Aktivitäten, die mit Geschäftszielen abgestimmt sind und auf Daten basieren.
1. **Priorisieren**: Rang und planen Sie Aktivitäten anhand der Ausrichtung des Unternehmens, des Aufwands und der potenziellen Auswirkungen.
1. **Design**: Erstellen Sie abgeschlossene Visualisierungen von Aktivitätserlebnissen und entwickeln Sie Aktivitätspläne mit detaillierten Kriterien.
1. **Erstellen und Ausführen**: Entwickeln Sie Aktivitäten, einschließlich [!DNL Target] Einrichtung, Codeentwicklung und QA-Tests.
1. **Analysieren**: Starten Sie die Aktivität [!DNL Target] für die Produktion und überwachen Sie die Leistung für die Dauer der Aktivität.
1. **Handeln und Iterieren**: Entwickeln Sie Empfehlungen basierend auf der Leistung der Test- oder Personalisierungsaktivität.

Da wir wissen, dass sich die Veränderung ständig ändert, sollte unsere Optimierungsstrategie ein iterativer Ausführungszyklus sein, um den sich ständig ändernden Anforderungen Ihrer Kunden gerecht zu werden (siehe Abbildung 1 unten).

![Optimierung und Personalisierung](assets/optimize-and-personalize.png)

_Abbildung 1: Iterativer Zyklus der Optimierung_

## Erstellen einer Optimierungsstrategie

Der Prozess der Entwicklung einer Optimierungsstrategie kann wie folgt unterteilt werden: (1) Erstellen eines Test-Aktivitätenplans und (2) Grundlegendes zur Optimierung.

1: Der Test-Aktivitätenplan sollte dokumentiert werden. Dadurch wird sichergestellt, dass Sie einen minimalen Qualitätsstandard in Bezug auf Ihre Test-Aktivitätsanwendung haben. Ihr Test-Aktivitätsplan sollte Folgendes umfassen:

* **Name und Beschreibung:** Intuitiver Aktivitätsname und Beschreibung dessen, worauf das Experiment konzentriert ist. &quot;Wie? Was? Wann? Wo? Warum?&quot;

* **Ziel:** Zweck der Aktivität und angeglichenes Geschäftsziel, auf das sie sich auswirken soll.

* **Hypothese:** Eine Hypothese ist eine Vorhersage, die Sie vor dem Ausführen eines Experiments erstellen. Es gibt klar, was getestet wird, was das Ergebnis sein wird und warum Sie denken, dass das der Fall ist. Wenn Sie das Experiment ausführen, wird Ihre Hypothese entweder beweisen oder widerlegt.

Eine vollständige Hypothese besteht aus drei Teilen:

* Wenn _variable_
* Dann _result_
* Weil _rationale_

* **Standort:** URL, Seitenabschnitt und Gerätetyp.
* **Zielmetrik:** Wie wird der Erfolg gemessen?
* **Sekundäre Metriken:** Andere wichtige Leistungsindikatoren (Key Performance Indicators, KPIs), die ausgewertet werden, um die Auswirkungen und Planungen besser zu verstehen.
* **Aktivitäts-Audience:** Beschreibung der erforderlichen Filterung der Testexposition.
* **Berichtszielgruppen:** Liste der Beschreibungen der für die Analyse zu verwendenden Besucheruntergruppen.
* **Erlebniskonzepte:** Modelle, Beispiele für Wireframes und Beschreibungen.

**Allgemeiner Hinweis:** Jedes Element einer Webseite, das den Geschäftswert steigern oder wertvolle Einblicke in das Besucherverhalten geben kann, kann getestet werden. Zu den gebräuchlichsten Testaktivitäten gehören:

* Überschriftentext
* Inhaltstext
* Schaltflächentext
* Seitenlayout
* Fotografie
* Schaltflächenfarbe
* Elementlayout
* Entfernen und Hinzufügen von Elementen
* Navigationsreihenfolge
* Navigationstaxonomie
* Suchschwerpunkt

2: Die zweite Phase der Strategie besteht darin, die Grundlagen der Optimierung zu verstehen, wozu auch das Verständnis der Testelemente selbst gehört. Zu den Testelementen der Optimierung gehören:

    A. Elementwert
    
    Dies wird erreicht, indem Sie einen Schritt zurück zur Frage gehen, warum ein bestimmtes Element auf Ihrer Site vorhanden ist und ob der Inhalt einem bestimmten Zweck dient. Diese Fragen sind ein guter Ausgangspunkt, wenn Ihre Site gerade eine Umgestaltung abgeschlossen hat oder wenn vor kurzem eine neue Funktion eingeführt wurde. Die zur Bestimmung des Elementwerts verwendete Taktik wird als Einschluss-/Ausschlusstests bezeichnet. Ein Einschluss-/Ausschlusstest bietet eine gute Werteseite auf der Seite, auf der das Element angezeigt wird.
    
    B. Elementdarstellung
    
    Hier sollten Sie über das Gesamterscheinungsbild des Elements und dessen Auswirkungen auf die Seitendarstellung nachdenken. Die für die Präsentation verwendete Taktik besteht darin, sich darauf zu konzentrieren, wirkungsvolle Änderungen an Inhalten und Elementseiten vorzunehmen.
    
    C. Elementfunktion
    
    Stellen wir hier die Frage, ob das Element auf der Seite das tut, was es tun soll? Ist die Interaktion erfolgreich und funktioniert sie wie gewünscht? Ist die Wechselwirkung natürlich oder ein Reibungspunkt? Die für die Funktion verwendete Taktik besteht darin, Erlebnisse zu erstellen, die sich auf benutzerfreundliche Funktionen ohne zusätzliche Kostenauswirkungen konzentrieren.

## Optimierung im Vergleich zur Personalisierung

Nachdem wir nun die Komponenten der Strategie analysiert und aufgelistet haben, ist es wichtig, zwischen Optimierungsbemühungen und Personalization-Bemühungen zu unterscheiden. Optimierung ist die Aktion, eine Situation oder Ressource optimal oder optimal zu nutzen, während Personalization die Aufgabe hat, etwas zu entwerfen oder zu produzieren, das den individuellen Anforderungen einer Person entspricht.

Auf hoher Ebene:

* Optimierung konzentriert sich auf Tests, um herauszufinden, was für ALLE, die mit Ihrer digitalen Präsenz interagieren, am effizientesten und leistungsfähigsten ist.
* Personalization testet, um herauszufinden, was für einige der Personen, die mit Ihrer digitalen Präsenz interagieren, am effizientesten und leistungsfähigsten ist.

Bei der Fokussierung auf die Optimierung sind die häufigsten Testaktivitäten:

* **A/B-Tests:** Echtzeit-Tests von zwei oder mehr Seiten oder Seitenelementen miteinander, um quantitative Einblicke in die Kundenpräferenz zu erhalten.
* **Multivarianz-Tests:** Vergleichen von Angebotskombinationen zwischen Elementen auf einer Seite, um zu sehen, welche Kombination die beste Leistung erzielt. Darüber hinaus ermittelt der Multivarianz-Test, welches Element der Seite die Konversionen am besten verbessert.

Wenn Sie sich auf Personalization konzentrieren, sehen Sie wahrscheinlich dieselben Testaktivitäten wie bei der Optimierung, aber sie sind auf spezifischere Zielgruppen ausgerichtet. Beispielsweise werden Sie bei A/B-Tests wahrscheinlich Seiten und Zielgruppen in den Erlebnissen hinzufügen, um Ihre Personalization weiter zu unterstützen.

Personalization umfasst auch den Aktivitätstyp Erlebnis-Targeting , mit dem Inhalte für bestimmte Zielgruppen basierend auf einem Satz definierter Regeln und Kriterien bereitgestellt werden. Wenn Sie mit dem Wachstum und der Vertiefung von Personalization beginnen, nutzen Sie hier auch einige der Premium-Funktionen von Target wie:

* Automated Personalization-Aktivitätstyp
* Art der Empfehlungsaktivitäten

## Optimierung vor der Personalisierung

In Anbetracht der obigen Kenntnisse empfiehlt Adobe, dass Sie Optimieren vornehmen, bevor Sie Personalization personalisieren, und von breit bis granular voranbringen. Um Personalization-Aktivitäten von breit bis detailliert zu gestalten, verwenden Sie zunächst einen Eins-zu-viele-Personalisierungsstil (breit gefasst) (mithilfe von A/B-Tests) und dann einen Eins-zu-Eins-Personalisierungsstil (granular) (mithilfe von automatisierten Personalisierungsaktivitäten).

Weitere Informationen finden Sie im [Webinar zum Verständnis und zur Optimierung Ihrer Adobe Target-Implementierung](https://adobecustomersuccess.adobeconnect.com/pkfafpzd9yarmp4/), in dem Sie mit Business Consultant, Katie Cozby, zusammenarbeiten.

Erfahren Sie mehr über Strategie und Gedankenführung am [Kundenerfolg](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html)-Hub.
