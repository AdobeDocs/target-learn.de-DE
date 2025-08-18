---
title: Schnellstart für Personalisierungstests und Erstellung von Roadmaps
description: Hier erfahren Sie mehr über ein Framework, mit dem Sie mit der Validierung von Personalisierungsaktivitäten beginnen und eine Personalisierungs-Roadmap erstellen können, die über Adobe Target und Adobe Analytics ausgeführt werden kann.
solution: Target,Analytics
level: Intermediate
role: Leader, Architect, Developer, Admin
exl-id: c0b6f9a0-7074-4e25-81e6-9781a54e2156
source-git-commit: 20bd1eb17ef6e287f7b76e14f727456e12d6f115
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 0%

---

# Schnellstart für Personalisierungstests und Erstellung von Roadmaps

Personalization kann leistungsstark sein, muss jedoch durch Tests validiert werden, um sicherzustellen, dass es wirklich den Wert steigert. Tests sind die effektivste Strategie, um festzustellen, wer, wie und was personalisiert werden sollte.

Zu Beginn des zweiten Jahrzehnts des 21. Jahrhunderts trennen sich Unternehmen wie das Ihre von veralteten Strategien zur Zielgruppenbestimmung und ungenauen Datenanalysen. Dies ist der Beginn der Personalisierung, einer Ära, in der die Verbraucher nicht weniger als ein benutzerdefiniertes Erlebnis erwarten. Personalization auf Unternehmensebene ist ein komplexer und sich ständig verändernder Prozess, aber wenn er effektiv durchgeführt wird, wird die Kundenzufriedenheit maximiert und der ROI erheblich erhöht.

Der folgende Artikel bietet ein Framework, mit dem Sie mit der Validierung von Personalisierungsaktivitäten beginnen und eine Personalisierungs-Roadmap erstellen können, die über Adobe Target und Adobe Analytics ausgeführt werden kann. Das Schnellstart-Framework von Adobe umfasst:

1. **Identifizieren von Personalisierungsmöglichkeiten** - Nutzen Sie die Datenanalyse, um Möglichkeiten zu identifizieren, sich auf wichtige Leistungsindikatoren auf Ihrer Site auszuwirken, die mit den Geschäftszielen Ihres Unternehmens verknüpft sind.

1. **Anwendungsfälle entwickeln** - Definieren Sie die Ziele Ihrer Personalisierungsaktivität unter Berücksichtigung spezifischer Besucherattribute. Seien Sie explizit, wie die kuratierten Inhalte das Besuchererlebnis verbessern werden, legen Sie im Voraus fest, wie der Erfolg aussehen wird und welche Aktionen aus den Testergebnissen ergriffen werden können.

1. **Erstellen einer Roadmap** - Aggregieren Sie eine Liste und priorisieren Sie Anwendungsfälle für die Personalisierung, stellen Sie sicher, dass sich Ihre Bemühungen auf hochwertige Aktivitäten konzentrieren. Gehen Sie davon aus, dass Sie Anwendungsfälle und Roadmaps basierend auf Erkenntnissen verfeinern und überarbeiten können.

1. **Erstellen und ausführen** - Erstellen und starten Sie die Adobe Target-Aktivitäten, um kuratierte Inhalte für Ihre Prioritätszielgruppen bereitzustellen.

1. **Ergreifen Sie Maßnahmen bezüglich der Ergebnisse** - Analysieren Sie die Performance der Aktivität und fassen Sie die Ergebnisse, Erkenntnisse, Empfehlungen und nächsten Schritte der Aktivität zusammen.

## Schritt 1: Identifizieren von Personalisierungsmöglichkeiten{#personalization}

Dies ist der Ausgangspunkt, an dem Sie die Personalization-Roadmap erstellen. Wenn Sie ein erfolgreiches Personalisierungsprogramm durchführen, müssen Sie sich auf Ihre wichtigsten Geschäftsziele und Leistungsindikatoren konzentrieren. Die Bemühungen von Personalization sollten entsprechend ausgerichtet werden, um einen Mehrwert zu erzielen. Paul Morris, Adobe Business Consultant, erklärt: „Wenn alles, was Sie tun, in diese Ziele einfließt, wird Ihr Programm höchstwahrscheinlich einen erheblichen Mehrwert erzielen. Wenn Sie jedoch einen vereinzelten Testansatz haben, werden Sie wahrscheinlich einige Erfolge erzielen, aber Ihr Gesamtprogramm wird nicht annähernd so erfolgreich sein.“

>[!NOTE]
>
>Wenn Sie nicht sofort wissen, was Ihre wichtigsten Geschäftsziele sind, ist es wichtig, sie so schnell wie möglich zu identifizieren. Achten Sie auf Folgendes:


* Stellen Sie eine Abstimmung zwischen Ihren Geschäftszielen und Ihrer umsetzbaren Hypothese her. Auf diese Weise können Sie Anwendungsfälle priorisieren, die für Ihr Unternehmen den größten Nutzen bieten.

* Machen Sie Ihre Ziele für Tracking-Zwecke messbar und korrelieren Sie mit den Auswirkungen auf den Umsatz.

* Die Ausrichtung jeder Opportunity sollte sich auf eine einzige Zielmetrik auswirken.

Manchmal haben Sie auch Ziele, die zunächst nicht greifbar erscheinen, wie z. B. Markenwert oder Loyalität. Es ist wichtig, dass Sie diese messen können, um sie als Zielmetriken für Personalization-Aktivitäten zu verwenden. In der Regel können diese Zieltypen weiterhin an den Auswirkungen auf den Umsatz angepasst werden, z. B. an den lebenslangen Kundennutzen oder die Anschaffungskosten. Achten Sie darauf, während Ihres Fortschritts die Programmleistung regelmäßig mit Ihren wichtigsten Geschäftszielen zu vergleichen, um sicherzustellen, dass Ihr Personalization-Programm von Nutzen ist.

Konzentrieren Sie die Datenanalyse, um bestimmte Bereiche Ihrer Website zu identifizieren, die verbessert werden können. Adobe empfiehlt, mit Adobe Analytics zu beginnen, um zielgerichtete Anwendungsfälle zu generieren. Wenn Sie über ein Analytics-Team verfügen, bitten Sie diese, sich Folgendes anzusehen:

1. Persönliche Pre-Form-Tabellen - Eine Ideenfunktion, die eine unbegrenzte Aufschlüsselung bietet und Ihnen bei der Beantwortung von Fragen oder Annahmen hilft, die Sie möglicherweise haben.
1. Erweiterte Segmentierung - Mit Segmentation IQ können Sie Besucher in verschiedenen Bereichen Ihrer Site vergleichen.
1. Juristische Bewertungen - Identifizieren Sie, welche Teile Ihrer Site am meisten von Personalization profitieren würden. Diese Bewertungen ermöglichen es Ihnen, einen Schritt zurück zu gehen und durch Ihre Website zu gehen, wie es ein Kunde tun würde.
1. Analyse der Konkurrenz - Wahrscheinlich stehen andere Unternehmen vor denselben Herausforderungen wie Sie. Diese Analyse ist nicht auf Unternehmen derselben Branche beschränkt.

Ziel dieses Schritts ist es, eine umsetzbare insight in Form einer Hypothese zu generieren. Eine Hypothese ist eine Prognose, die Sie vor der Durchführung eines Experiments erstellen. Es sagt klar, was geändert wird, was das Ergebnis Ihrer Meinung nach sein wird und warum Sie denken, dass das der Fall ist. Die Durchführung des Experiments bestätigt oder widerlegt Ihre Hypothese. Am Ende dieses Schritts sollten Sie eine Reihe von Hypothesen für Personalisierungsmöglichkeiten haben, die Ihre Website und die Zufriedenheit Ihrer Besucher verbessern.

## Schritt 2: Anwendungsfälle entwickeln{#use-cases}

Beginnen Sie mit den in Schritt 1 generierten Hypothesen und entwickeln Sie dann Ihre Aktivitäten darum herum. Jetzt können Sie die in Schritt 1A erstellten Vorformtabellen entwickeln. Jeder der KPIs verfügt über eine Reihe von Hypothesen, die dann zu individuellen Tests innerhalb von Adobe Target werden. Wenn Sie Schwierigkeiten haben, an diesen Punkt zu gelangen, beginnen Sie so einfach wie möglich, zum Beispiel sich auf die wiederkehrenden Besucher zu konzentrieren, die Ihre Website besuchen. Denken Sie darüber nach, wie Sie Ihre Homepage an Ihre wiederkehrenden Besucher anpassen können. Nachdem Sie Ihren Satz von Hypothesen haben, müssen Sie jede Aktivität definieren, um jeden Anwendungsfall effektiv zu priorisieren.

1. Definieren Sie die prioritären Zielgruppen, denen Sie personalisierte Inhalte bereitstellen möchten, und achten Sie dabei auf die Unique-Visitor-Attribute, die definieren, wer sie sind und was sie möchten (z. B. Bestandskunde vs. Interessent). Die Wünsche und Bedürfnisse der prioritären Zielgruppen sollten mit Ihren Geschäftszielen übereinstimmen

1. Ermitteln Sie den spezifischen Ort auf der Journey des Besuchers, an dem personalisierte Inhalte die größte Wirkung haben. Konzentrieren Sie sich auf Seiten, auf denen Sie Besucher verschiedener Rollen oder mit unterschiedlichen Bedürfnissen/Absichten erwarten würden.

1. Beginnen Sie mit der Planung einiger Design-Arbeiten Ihrer Variante. Inhalte sollten sorgfältig entsprechend den spezifischen Anforderungen und Wünschen der Zielgruppe kuratiert werden, wobei zu berücksichtigen ist, wo sie sich auf ihrem Journey befinden. Der richtige Inhalt sollte klar abgegrenzt und differenziert sein.

## Schritt 3: Erstellen einer Roadmap, Aggregieren und Priorisieren von Anwendungsfällen

Aggregieren Sie eine umfassende Liste von Personalisierungsmöglichkeiten, die mindestens den Ort, die Idee und die Priorität der Personalisierungsaktivitäten erfasst.

Der Schritt „Priorisierung“ ist in zwei Faktoren unterteilt:

**Wert:** Nutzen Sie Branchenforschung, Benchmarking und ähnliche Anwendungsfälle aus der Vergangenheit, um den erwarteten Wert jeder Ihrer Hypothesen zu verstehen. Sie möchten, dass Ihr Wert direkt mit einem Ihrer wichtigsten Geschäftsergebnisse (Key Business Outcomes, KBOs) verknüpft wird und in einem Standardformat vorliegt, sodass jeder Ihrer Anwendungsfälle miteinander verglichen werden kann. Die häufigste Methode besteht darin, auf jeden Anwendungsfall einen Geldwert zum Vergleich anzuwenden.

* Kosten - Die Erstellung Ihrer Design-Varianten in Target und der anschließende potenzielle Rollout verursachen natürliche Kosten. Jetzt müssen Sie die mit jedem Anwendungsfall verbundenen Kosten schätzen. Die Kosten umfassen den Zeit- und Ressourcenaufwand für den Aufbau von Testerlebnissen, die Planung und die Analyse nach dem Test.

Adobe empfiehlt, jeden Ihrer Anwendungsfälle nach einer Skala von 1 bis 5 zu ordnen, wobei 1 einfach und 5 komplex sein sollten. Jetzt verfügen Sie über eine Reihe priorisierter Aktivitäten, die Sie in Adobe Target testen können. Diese Aktivitäten bilden die Grundlage für Ihre jährlichen Personalisierungsaktivitäten. Adobe empfiehlt, die Personalization-Roadmap regelmäßig zu überprüfen. Die Erkenntnisse aus den einzelnen Aktivitäten sollten sich auf Ihre zukunftsgerichteten Roadmap-Prioritäten auswirken. Erkenntnisse und Empfehlungen werden wirkungsvoller sein, wenn sie rechtzeitig umgesetzt werden. Die Prioritäten können sich über das ganze Jahr ändern, aber die Durchführung einer iterativen Methode stellt sicher, dass Sie immer einen strategischen Aktionsplan haben und dass Sie Ihre Team- und Unternehmensziele verfolgen können.

## Schritt 4: Entwurf und Ausführung

Erstellen Sie mithilfe der erstellten Dokumentation für den Anwendungsfall Personalisierung die Personalization-Aktivität in Target, um kuratierte Inhalte für Ihre Prioritätszielgruppen bereitzustellen. Stellen Sie sicher, dass der Aktivitätstyp, die Einstellungen, Erlebnisse und Reporting-Funktionen auf die Ziele des Anwendungsfalls abgestimmt sind. Design, Qualitätssicherung und Launch Ihrer Personalisierungsstrategie sind am effizientesten, wenn sie in bestehende Unternehmensprozesse einfließen.

## Schritt 5: Ergebnisse optimieren

Sobald Ihre Personalisierungsaktivität eine repräsentative Stichprobe von Besuchern erreicht hat, können Sie mit der Analyse beginnen, indem Sie die Einblicke nutzen, um die nächsten Schritte zu leiten. Daten in Ihrer Analyse zu berücksichtigen, Empfehlungen mit Ihrer Anwendungsfallhypothese zu verknüpfen und die Auswirkungen auf Geschäftsziele klar zu veranschaulichen.

### Weitere Informationen

Wir empfehlen, sich dieses Video anzusehen, in dem die einzelnen Schritte erläutert werden: [https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/](https://adobecustomersuccess.adobeconnect.com/pvsqvdvunpai/)

Erfahren Sie mehr über Strategie und Meinungsführerschaft auf dem [Customer Success](https://experienceleague.adobe.com/docs/customer-success/customer-success/overview.html?lang=de)-Hub.