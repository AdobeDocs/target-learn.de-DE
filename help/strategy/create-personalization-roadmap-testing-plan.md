---
title: QuickStart für Personalisierungstests und Roadmap-Erstellung
description: Erfahren Sie, mit welchem Framework Sie mit der Validierung von Personalisierungsaktivitäten und der Erstellung einer Personalisierungs-Roadmap beginnen können, die über Adobe Target und Adobe Analytics ausgeführt wird.
solution: Target,Analytics
level: Intermediate
role: Leader, Architect, Developer, Admin
exl-id: c0b6f9a0-7074-4e25-81e6-9781a54e2156
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 0%

---

# QuickStart für Personalisierungstests und Roadmap-Erstellung

Personalization kann leistungsstark sein, muss aber durch Tests überprüft werden, um sicherzustellen, dass es wirklich einen Mehrwert bringt. Testen ist die effektivste Strategie, um herauszufinden, wer, wie und was Sie personalisieren sollten.

Mit dem Beginn des zweiten Jahrzehnts des 21. Jahrhunderts unterteilen Organisationen wie Ihre Wege mit veralteten Zielgruppenstrategien für Verbraucher und ungenauen Datenanalysen. Dies ist der Beginn der Personalisierung, einer Ära, in der die Verbraucher nicht weniger als ein benutzerspezifisches Erlebnis erwarten. Personalization auf Unternehmensebene ist ein komplexer und sich ständig ändernder Prozess, aber wenn dies effektiv durchgeführt wird, wird es die Kundenzufriedenheit maximieren und den ROI deutlich steigern.

Der folgende Artikel bietet ein Framework, mit dem Sie mit der Validierung von Personalisierungsaktivitäten und der Erstellung einer Personalisierungs-Roadmap beginnen können, die über Adobe Target und Adobe Analytics ausgeführt werden kann. Adobe QuickStart-Framework beinhaltet:

1. **Identifizieren von Personalisierungsmöglichkeiten** - Nutzen Sie die Datenanalyse, um festzustellen, welche Möglichkeiten sich auf wichtige Leistungsindikatoren auf Ihrer Site auswirken, die mit den Geschäftszielen Ihres Unternehmens in Verbindung stehen.

1. **Anwendungsfälle entwickeln** - Legen Sie Ziele Ihrer Personalisierungsaktivität mit bestimmten Besucherattributen fest, geben Sie explizit an, wie der kuratierte Inhalt das Erlebnis des Besuchers verbessert, legen Sie im Voraus fest, wie der Erfolg aussehen wird und welche Aktionen aus den Testergebnissen durchgeführt werden können.

1. **Erstellen einer Roadmap** - Aggregieren Sie eine Liste und priorisieren Sie Anwendungsfälle für Personalisierungen, stellen Sie sicher, dass Ihre Bemühungen auf Aktivitäten mit hohem Wert ausgerichtet sind. Verfeinern und überarbeiten Sie Anwendungsfälle und erstellen Sie basierend auf den Erkenntnissen eine Roadmap.

1. **Entwerfen und Ausführen** - Erstellen und starten Sie die Adobe Target-Aktivitäten, um kuratierte Inhalte für Ihre prioritären Zielgruppen bereitzustellen.

1. **Ergreifen Sie Maßnahmen zu Ergebnissen** - Analysieren Sie die Aktivitätsleistung und fassen Sie die Aktivitätsergebnisse, Einblicke, Empfehlungen und nächsten Schritte zusammen.

## Schritt 1: Identifizieren von Personalisierungsmöglichkeiten{#personalization}

Dies ist der Ausgangspunkt für die Erstellung des Personalization-Fahrplans. Bei der Durchführung eines erfolgreichen Personalisierungsprogramms ist es wichtig, sich auf Ihre wichtigsten Geschäftsziele und Leistungsindikatoren zu konzentrieren. Die Bemühungen der Personalization sollten entsprechend ausgerichtet werden, um einen Mehrwert zu erzielen. Paul Morris, Adobe Business Consultant, erklärt: &quot;Wenn alles, was Sie tun, in diese Ziele eingebunden wird, wird Ihr Programm höchstwahrscheinlich einen erheblichen Mehrwert bringen. Wenn Sie jedoch einen verstreuten Testansatz haben, werden Sie wahrscheinlich einige Siege finden, aber Ihr Gesamtprogramm wird nicht annähernd so erfolgreich sein.&quot;

>[!NOTE]
>
>Wenn Sie nicht sofort wissen, was Ihre wichtigsten Geschäftsziele sind, ist es wichtig, sie so bald wie möglich zu identifizieren. Stellen Sie Folgendes sicher:


* Stellen Sie die Abstimmung zwischen Ihren Geschäftszielen und Ihrer umsetzbaren Hypothese her. Auf diese Weise können Sie Anwendungsfälle priorisieren, die für Ihr Unternehmen den größtmöglichen Nutzen bringen.

* Ihre Ziele für Tracking-Zwecke messbar machen und mit den Auswirkungen auf den Umsatz korrelieren.

* Die Ausrichtung jeder Gelegenheit sollte sich auf eine einzige Zielmetrik auswirken.

Manchmal haben Sie auch Ziele, die anfangs nicht greifbar erscheinen, wie z. B. Markenwert oder Loyalität. Es ist wichtig, dass Sie diese Metriken messen können, um sie als Zielmetriken für Personalization-Aktivitäten zu verwenden. In der Regel können diese Zieltypen immer noch an die Auswirkungen auf den Umsatz angepasst werden, wie z. B. der Kundenwert über die gesamte Lebensdauer oder die Akquisekosten. Achten Sie dabei darauf, die Programmleistung regelmäßig an Ihre wichtigsten Geschäftsziele anzupassen, um sicherzustellen, dass Ihr Personalization-Programm einen Mehrwert bietet.

Konzentrieren Sie die Datenanalyse, um spezifische Bereiche Ihrer Website zu ermitteln, die verbessert werden können. Adobe empfiehlt, mit Adobe Analytics zu beginnen, um gezielte Anwendungsfälle zu generieren. Wenn Sie über ein Analytics-Team verfügen, bitten Sie diese, sich Folgendes anzusehen:

1. Persönliche Tabellen vor dem Formular - Eine Ideenfunktion, die eine unbegrenzte Aufschlüsselung bietet und Ihnen bei der Beantwortung von Fragen oder Annahmen helfen kann, die möglicherweise bei Ihnen auftreten.
1. Erweiterte Segmentierung - Segmentierung IQ ermöglicht Ihnen, Besucher über verschiedene Abschnitte Ihrer Site hinweg zu vergleichen.
1. Rechtsbezogene Bewertungen - Ermitteln Sie, welche Teile Ihrer Site von Personalization am meisten profitieren würden. Diese Bewertungen ermöglichen es Ihnen, einen Schritt zurück zu gehen und wie ein Kunde Ihre Website zu besuchen.
1. Konkurrentenanalyse - Wahrscheinlich stehen auch andere Unternehmen vor denselben Herausforderungen wie Sie. Diese Analyse ist nicht auf Unternehmen desselben Wirtschaftszweigs beschränkt.

Ziel dieses Schritts ist es, umsetzbare Einblicke in Form einer Hypothese zu generieren. Eine Hypothese ist eine Vorhersage, die Sie vor dem Ausführen eines Experiments erstellen. Es zeigt klar, was geändert wird, was Sie glauben, dass das Ergebnis sein wird und warum Sie denken, dass das der Fall ist. Wenn Sie das Experiment ausführen, wird Ihre Hypothese entweder beweisen oder widerlegt. Am Ende dieses Schritts sollten Sie eine Reihe von Hypothesen für Personalisierungsmöglichkeiten haben, die Ihre Website und die Besucherzufriedenheit verbessern.

## Schritt 2: Anwendungsfälle entwickeln{#use-cases}

Beginnen Sie mit den Hypothesen, die in Schritt 1 generiert wurden, und entwickeln Sie dann Ihre Aktivitäten um sie herum. Jetzt können Sie die in Schritt 1A erstellten Preform-Tabellen entwickeln. Jeder der KPIs verfügt über eine Reihe von Hypothesen, die dann in Adobe Target zu individuellen Tests werden. Wenn Sie Schwierigkeiten haben, zu diesem Punkt zu gelangen, beginnen Sie so einfach wie möglich, z. B. mit der Konzentration auf die wiederkehrenden Besucher, die Ihre Site häufig besuchen. Denken Sie darüber nach, wie Sie Ihre Homepage an Ihre wiederkehrenden Besucher anpassen können. Sobald Sie über einen Satz Hypothesen verfügen, müssen Sie jede Aktivität definieren, um jeden Anwendungsfall effektiv zu priorisieren.

1. Definieren Sie die prioritären Zielgruppen, denen Sie personalisierte Inhalte bereitstellen möchten, wobei Sie die Unique Visitor-Attribute berücksichtigen, die definieren, wer sie sind und was sie wollen (z. B. Bestandskunde vs. potenzieller Kunde). Die Anforderungen und Bedürfnisse der vorrangigen Zielgruppen sollten mit Ihren Geschäftszielen übereinstimmen.

1. Identifizieren Sie die spezifische Stelle auf der Journey des Besuchers, an der personalisierter Inhalt am wirkungsvollsten sein wird. Konzentrieren Sie sich auf Seiten, von denen Sie erwarten würden, dass Besucher unterschiedlicher Personas oder Besucher mit unterschiedlichen Bedürfnissen/Inhalten auftreten.

1. Beginnen Sie mit der Planung einiger Designarbeiten Ihrer Variante. Die Inhalte sollten entsprechend den jeweiligen Anforderungen und Wünschen der Zielgruppe sorgfältig kuratiert werden, wobei zu berücksichtigen ist, wo sie sich auf ihrer Journey befinden. Der richtige Inhalt sollte klar und differenziert sein.

## Schritt 3: Erstellen einer Roadmap, Aggregation und Priorisierung von Anwendungsfällen

Aggregieren Sie eine umfassende Liste von Personalisierungsmöglichkeiten, die mindestens Ort, Idee und Priorität der Personalisierungsaktivitäten erfasst.

Der Schritt &quot;Priorisierung&quot;ist in zwei Faktoren unterteilt:

**Wert:** Nutzen Sie die Branchenforschung, das Benchmarking und ähnliche Anwendungsfälle aus der Vergangenheit, um den erwarteten Wert zu verstehen, den jede Ihrer Hypothesen bringen kann. Sie möchten, dass Ihr Wert direkt mit einem Ihrer wichtigsten geschäftlichen Ergebnisse (Key Business Outcome, KBOs) verknüpft ist und in einem Standardformat vorliegt, sodass jeder Ihrer Anwendungsfälle miteinander verglichen werden kann. Die gängigste Methode besteht darin, für jeden Anwendungsfall zum Vergleich einen Geldwert anzuwenden.

* Kosten - Die Erstellung Ihrer Designvarianten in Target und die anschließende Einführung in Target verursachen natürliche Kosten. Jetzt müssen Sie die mit jedem Anwendungsfall verbundenen Kosten abschätzen. Die Kosten umfassen die Zeit und Ressourcen, die zum Erstellen von Testerlebnissen, zur Planung und zur Analyse nach dem Test erforderlich sind.

Adobe empfiehlt, jeden Ihrer Anwendungsfälle auf einer Skala von 1-5 zu bewerten, wobei 1 einfach und 5 komplex ist. Sie verfügen jetzt über eine Reihe priorisierter Aktivitäten, die Sie in Adobe Target testen können. Diese Aktivitäten bilden die Grundlage Ihrer jährlichen Personalisierungsaktivitäten. Adobe empfiehlt, den Personalization-Fahrplan regelmäßig neu zu bewerten. Die Erkenntnisse aus den einzelnen Aktivitäten sollten Ihre vorausschauenden Fahrplan-Prioritäten beeinflussen. Lehren und Empfehlungen werden wirkungsvoller sein, wenn sie rechtzeitig bearbeitet werden. Die Prioritäten im Laufe des Jahres können sich ändern, aber die Durchführung einer iterativen Methodik stellt sicher, dass Sie stets einen strategischen Aktionsplan haben und dass Sie Ihre Team- und Unternehmensziele verfolgen können.

## Schritt 4: Erstellen und Ausführen

Mithilfe der erstellten Dokumentation zur Strategiestrategie des Anwendungsfalls der Personalisierung können Sie die Personalization-Aktivität in Target erstellen, um kuratierte Inhalte für Ihre prioritären Zielgruppen bereitzustellen. Stellen Sie sicher, dass der Aktivitätstyp, die Einstellungen, Erlebnisse und Berichterstattungsfunktionen an den Zielen des Anwendungsfalls ausgerichtet sind. Design, QA und Launch Ihrer Personalisierungsanstrengungen sind am effizientesten, wenn die vorhandenen Unternehmensprozesse berücksichtigt werden.

## Schritt 5: Ergreifen Sie Maßnahmen bezüglich der Ergebnisse.

Sobald Ihre Personalisierungsaktivität eine repräsentative Stichprobe von Besuchern eingebunden hat, können Sie mit der Analyse beginnen und dabei die Einblicke nutzen, die als Leitfaden für die nächsten Schritte dienen. Seien Sie bei Ihrer Analyse datenorientiert, binden Sie Empfehlungen an Ihre Anwendungsfallhypothese und veranschaulichen Sie die Auswirkungen auf die Geschäftsziele.

### Weitere Informationen

Es wird empfohlen, sich dieses Video anzusehen, in dem die einzelnen Schritte erläutert werden: [https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/](https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/)

Erfahren Sie mehr über Strategie und Gedankenführung am [Kundenerfolg](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html)-Hub.