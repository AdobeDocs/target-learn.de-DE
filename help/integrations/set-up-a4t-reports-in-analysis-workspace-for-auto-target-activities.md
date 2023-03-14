---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] Tätigkeiten
description: Konfigurieren von A4T-Berichten in [!DNL Analysis Workspace] zum Abrufen der erwarteten Ergebnisse während der Ausführung [!UICONTROL Automatisches Targeting] Aktivitäten?
badgePremium: label="Premium" type="Positive" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en#premium newtab=true" tooltip="See what's included in Target Premium."
badgeBeta: label="Beta" type="Informative" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en#beta newtab=true" tooltip="What are Target Beta release features?"
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
thumbnail: null
kt: null
exl-id: 58006a25-851e-43c8-b103-f143f72ee58d
source-git-commit: 0ab5bc8b2ad4b5b32069b022d95d0862ec84e868
workflow-type: tm+mt
source-wordcount: '2253'
ht-degree: 1%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] activities

>[!IMPORTANT]
>
>Für [!UICONTROL Automatisches Targeting] Aktivitäten, müssen Sie die Berichterstellung unter [!DNL Analytics Workspace] und erstellen Sie manuell ein A4T-Bedienfeld.

Die [!UICONTROL Analytics for Target] (A4T)-Integration für [!DNL Auto-Target] -Aktivitäten verwendet die [!DNL Adobe Target] Sie können Algorithmen des maschinellen Lernens (ML) verwenden, um basierend auf Profil, Verhalten und Kontext das beste Erlebnis für jeden Besucher auszuwählen, während Sie gleichzeitig eine [!DNL Adobe Analytics] Zielmetrik.

Obwohl Rich-Analytics-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace], einige Änderungen an der Standardeinstellung **[!UICONTROL Analytics for Target]** -Bedienfeld zur korrekten Interpretation erforderlich [!DNL Auto-Target] Aktivitäten aufgrund von Unterschieden zwischen Experimentieraktivitäten (manuelles [!UICONTROL A/B-Test] und [!UICONTROL Automatische Zuordnung]) und Personalisierungsaktivitäten ([!UICONTROL [!UICONTROL Automatisches Targeting]]).

Dieses Tutorial führt Sie durch die empfohlenen Änderungen zur Analyse [!UICONTROL Automatisches Targeting] Aktivitäten in [!DNL Analysis Workspace], die auf den folgenden Schlüsselkonzepten basieren:

* Die **[!UICONTROL Kontrolle im Vergleich zu Zielgruppe]** -Dimension verwendet werden, um zwischen [!UICONTROL Kontrolle] Erlebnisse im Vergleich zu denen, die von der [!UICONTROL Automatisches Targeting] den ML-Algorithmus.
* Besuche sollten bei der Anzeige von Leistungsunterteilungen auf Erlebnisebene als Normalisierungsmetrik verwendet werden. Darüber hinaus [Die Standardzählmethodik von Adobe Analytics kann Besuche umfassen, bei denen der Benutzer keine Aktivitätsinhalte sieht](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html?lang=en#metrics), dieses Standardverhalten kann jedoch mithilfe eines entsprechend abgegrenzten Segments geändert werden (Details unten).
* Die Attribution mit Besuchs-Lookback, auch als &quot;Besuchs-Lookback-Fenster&quot;im vorgeschriebenen Attributionsmodell bezeichnet, wird von der [!DNL Adobe Target] ML-Modelle während ihrer Schulungsphasen und dasselbe (nicht standardmäßige) Attributionsmodell sollten bei der Unterteilung der Zielmetrik verwendet werden.

## Erstellen Sie A4T für [!UICONTROL Automatisches Targeting] Bedienfeld in [!DNL Analysis Workspace]

So erstellen Sie A4T für [!UICONTROL Automatisches Targeting] entweder mit der **[!UICONTROL Analytics for Target]** Bedienfeld in [!DNL Analysis Workspace], wie unten dargestellt, oder beginnen Sie mit einer Freiformtabelle. Wählen Sie dann die folgenden Optionen aus:

1. **[!UICONTROL Kontrollerlebnis]**: Sie können ein beliebiges Erlebnis auswählen. Sie werden diese Auswahl jedoch später überschreiben. Beachten Sie Folgendes: [!UICONTROL Automatisches Targeting] -Aktivitäten ist das Kontrollerlebnis tatsächlich eine Kontrollstrategie, die entweder a) zufällig unter allen Erlebnissen bereitgestellt wird oder b) ein einziges Erlebnis bereitstellt (diese Auswahl erfolgt zum Zeitpunkt der Aktivitätserstellung in [!DNL Adobe Target]). Selbst wenn Sie sich für die Wahl (b) entschieden haben, wird Ihre [!UICONTROL Automatisches Targeting] -Aktivität ein bestimmtes Erlebnis als Kontrolle bezeichnet. Sie sollten weiterhin den in diesem Tutorial zur Analyse von A4T für [!UICONTROL Automatisches Targeting] Aktivitäten.
2. **[!UICONTROL Normalisierungsmetrik]**: Auswählen [!UICONTROL Besuche].
3. **[!UICONTROL Erfolgsmetriken]**: Obwohl Sie beliebige Metriken auswählen können, für die Berichte erstellt werden sollen, sollten Sie im Allgemeinen Berichte zu derselben Metrik anzeigen, die bei der Aktivitätserstellung in [!DNL Target].

   ![[!UICONTROL Analytics for Target] Bedienfeldeinstellungen für [!UICONTROL Automatisches Targeting] Aktivitäten.](assets/Figure1.png)

   *Abbildung 1: [!UICONTROL Analytics for Target] Bedienfeldeinstellungen für [!UICONTROL Automatisches Targeting] Aktivitäten.*

>[!TIP]
>
>So richten Sie [!UICONTROL Analytics for Target] Bereich für [!UICONTROL Automatisches Targeting] Aktivitäten, beliebiges Kontrollerlebnis auswählen, [!UICONTROL Besuche] als Normalisierungsmetrik verwenden und dieselbe Zielmetrik auswählen, die während der [!DNL Target] Aktivitätserstellung.

## Verwenden Sie die [!UICONTROL Kontrolle vs. Targeting] Dimension zum Vergleich [!DNL Target] ML-Modell für Ihr Steuerelement zusammenführen

Das standardmäßige A4T-Bedienfeld wurde für klassische (manuelle) Bedienfelder entwickelt. [!UICONTROL A/B-Test] oder [!UICONTROL Automatische Zuordnung] Aktivitäten, bei denen das Ziel darin besteht, die Leistung einzelner Erlebnisse mit dem Kontrollerlebnis zu vergleichen. In [!UICONTROL Automatisches Targeting] -Aktivitäten, sollte jedoch der erste Sortiervergleich zwischen der Kontrollgruppe *strategy* und die Zielgruppe *strategy*. Mit anderen Worten, die Ermittlung der Steigerung der Gesamtleistung der [!UICONTROL Automatisches Targeting] das ML-Modell über die Kontrollstrategie.

Verwenden Sie für diesen Vergleich die **[!UICONTROL Kontrolle vs. Targeting (Analytics für Target)]** Dimension. Ziehen und ablegen , um die **[!UICONTROL Target-Erlebnisse]** -Dimension im standardmäßigen A4T-Bericht.

Beachten Sie, dass diese Ersetzung die Standardeinstellung ungültig macht. [!UICONTROL Steigerung und Konfidenz] Berechnungen im A4T-Bedienfeld. Um Verwirrung zu vermeiden, können Sie diese Metriken aus dem Standardbereich entfernen und den folgenden Bericht beibehalten:

![[!UICONTROL Erlebnisse nach Aktivitätskonversionen] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure2.png)

*Abbildung 2: Der empfohlene Ausgangsbericht für [!DNL Auto-Target] Aktivitäten. Dieser Bericht wurde so konfiguriert, dass zielgerichteter Traffic (bereitgestellt vom Ensemble ML-Modell) mit Ihrem Kontroll-Traffic verglichen wird.*

>[!NOTE]
>
>Zurzeit [!UICONTROL Steigerung und Konfidenz] -Zahlen stehen nicht zur Verfügung für [!UICONTROL Kontrolle im Vergleich zu Zielgruppe] Dimensionen für A4T-Berichte für [!UICONTROL Automatisches Targeting]. Bis die Unterstützung hinzugefügt wird, [!UICONTROL Steigerung und Konfidenz] kann manuell berechnet werden, indem die [Vertrauensrechner](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx?lang=en).

## Aufschlüsselungen von Metriken auf Erlebnisebene hinzufügen

Um weitere Einblicke in die Leistung des ML-Ensemble-Modells zu erhalten, können Sie die Aufschlüsselungen auf Erlebnisebene der **[!UICONTROL Kontrolle im Vergleich zu Zielgruppe]** Dimension. In [!DNL Analysis Workspace], ziehen Sie die **[!UICONTROL Target-Erlebnisse]** in den Bericht ein und unterteilen dann jede Kontroll- und Zielgruppendimension separat.

![[!UICONTROL Erlebnisse nach Aktivitätskonversionen] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure3.png)

*Abbildung 3: Aufschlüsseln der Zielgruppendimension nach Target-Erlebnissen*

Ein Beispiel für den resultierenden Bericht finden Sie hier.

![[!UICONTROL Erlebnisse nach Aktivitätskonversionen] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure4.png)

*Abbildung 4: Ein Standard [!UICONTROL Automatisches Targeting] Berichte mit Aufschlüsselungen auf Erlebnisebene erstellen. Beachten Sie, dass Ihre Zielmetrik möglicherweise anders ist und Ihre Kontrollstrategie über ein einziges Erlebnis verfügen kann.*

>[!TIP]
>
>In [!DNL Analysis Workspace]klicken Sie auf das Zahnradsymbol, um die Prozentsätze im [!UICONTROL Konversionsrate] -Spalte, um den Fokus weiterhin auf die Erlebniskonversionsraten zu legen. Die Konversionsraten werden dann als Dezimalzahlen formatiert, aber entsprechend als Prozentsätze interpretiert.

## Warum[!UICONTROL Besuche]&quot; ist die richtige Normalisierungsmetrik für [!UICONTROL Automatisches Targeting] activities

Bei der Analyse einer [!UICONTROL Automatisches Targeting] Aktivität, immer wählen [!UICONTROL Besuche] als standardmäßige Normalisierungsmetrik. [!UICONTROL Automatisches Targeting] Personalisierung wählt ein Erlebnis für einen Besucher einmal pro Besuch aus (formell einmal pro Besuch [!DNL Target] Sitzung), was bedeutet, dass sich das einem Besucher angezeigte Erlebnis bei jedem einzelnen Besuch ändern kann. Wenn Sie [!UICONTROL Unique Visitors] als Normalisierungsmetrik verwendet wird, würde die Tatsache, dass einem einzelnen Benutzer (über verschiedene Besuche hinweg) am Ende mehrere Erlebnisse angezeigt werden, zu verwirrenden Konversionsraten führen.

Ein einfaches Beispiel zeigt diesen Punkt: betrachten ein Szenario, in dem zwei Besucher an einer Kampagne teilnehmen, die nur über zwei Erlebnisse verfügt. Der erste Besucher besucht zweimal. Sie werden Erlebnis A beim ersten Besuch, Erlebnis B beim zweiten Besuch zugewiesen (da sich ihr Profilstatus bei diesem zweiten Besuch ändert). Nach dem zweiten Besuch wandelt der Besucher durch eine Bestellung um. Die Konversion wird dem zuletzt angezeigten Erlebnis (Erlebnis B) zugeordnet. Der zweite Besucher besucht auch zweimal. Erlebnis B wird beide Male angezeigt, jedoch nie konvertiert.

Vergleichen wir Berichte auf Besucher- und Besuchsebene:

| Erlebnis | Unique Visitors | Besuche | Konversionen | Besuchernormalisierte Konversionsrate | Besuchsnormalisierte Konversionsrate |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33.3% |
| Gesamt | 2 | 4 | 1 | 50% | 25 % |

*Tabelle 1: Beispiel für den Vergleich von besuchernormalisierten und besuchsnormalisierten Berichten für ein Szenario, in dem Entscheidungen an einen Besuch gebunden sind (und nicht an Besucher, wie bei regulären A/B-Tests). Besuchernormalisierte Metriken verwirren in diesem Szenario.*

Wie in der Tabelle gezeigt, besteht eine eindeutige Unstimmigkeit zwischen Zahlen auf Besucherebene. Obwohl es insgesamt zwei Unique Visitors gibt, handelt es sich hierbei nicht um eine Summe einzelner Unique Visitors für jedes Erlebnis. Auch wenn die Konversionsrate auf Besucherebene nicht unbedingt falsch ist, ergeben Konversionsraten auf Besuchsebene beim Vergleich einzelner Erlebnisse wohl deutlich mehr Sinn. Formell entspricht die Analyseeinheit (&quot;Besuche&quot;) der Entscheidungs-Treue, was bedeutet, dass Aufschlüsselungen von Metriken auf Erlebnisebene hinzugefügt und verglichen werden können.

## Filtern nach tatsächlichen Besuchen der Aktivität

Die [!DNL Adobe Analytics] Standardzählmethodik für Besuche bei einer [!DNL Target] Die Aktivität kann Besuche umfassen, bei denen der Benutzer nicht mit der [!DNL Target] Aktivität. Dies ist auf die [!DNL Target] Aktivitätszuweisungen werden im [!DNL Analytics] Besucherkontext. Die Anzahl der Besuche bei der [!DNL Target] Die Aktivität kann in manchen Fällen überhöht sein, was zu einem Rückgang der Konversionsraten führt.

Wenn Sie Berichte zu Besuchen bevorzugen, bei denen der Benutzer tatsächlich mit der [!UICONTROL Automatisches Targeting] -Aktivität (entweder durch Einstieg in die Aktivität, ein Anzeige-, Besuchsereignis oder eine Konversion) können Sie:

1. Erstellen Sie ein bestimmtes Segment, das Treffer aus dem [!DNL Target] die betreffende Aktivität und
1. Filtern Sie die [!UICONTROL Besuche] Metrik mithilfe dieses Segments.

**So erstellen Sie das Segment:**

1. Wählen Sie die **[!UICONTROL Komponenten > Segment erstellen]** in der [!DNL Analysis Workspace] Symbolleiste.
2. Geben Sie eine **[!UICONTROL Titel]** für Ihr Segment. Im unten gezeigten Beispiel heißt das Segment [!DNL "Hit with specific Auto-Target activity"].
3. Ziehen Sie die **[!UICONTROL Target Activities]** Dimension zum Segment **[!UICONTROL Definition]** Abschnitt.
4. Verwenden Sie die **[!UICONTROL gleich]** Operator.
5. Suchen Sie nach Ihren spezifischen [!DNL Target] Aktivität.
6. Klicken Sie auf das Zahnradsymbol und wählen Sie **[!UICONTROL Attributionsmodell > Instanz]** wie in der folgenden Abbildung dargestellt.
7. Klicken Sie auf **[!UICONTROL Speichern]**.

![Segment in [!DNL Analysis Workspace]](assets/Figure5.png)

*Abbildung 5: Verwenden Sie ein Segment wie das hier angezeigte, um die [!UICONTROL Besuche] Metrik in Ihrem A4T für [!UICONTROL Automatisches Targeting] Bericht*

Nachdem das Segment erstellt wurde, verwenden Sie es zum Filtern der [!UICONTROL Besuche] Metrik, also die [!UICONTROL Besuche] Metrik umfasst nur Besuche, bei denen der Benutzer mit der [!DNL Target] Aktivität.

**Filter [!UICONTROL Besuche] mithilfe dieses Segments:**

1. Ziehen Sie das neu erstellte Segment aus der Komponenten-Symbolleiste und bewegen Sie den Mauszeiger über die Basis der **[!UICONTROL Besuche]** Metrikbezeichnung bis zu einem blauen **[!UICONTROL Filtern nach]** wird angezeigt.
2. Lassen Sie das Segment frei. Der Filter wird auf diese Metrik angewendet.

Das endgültige Bedienfeld wird wie folgt angezeigt:

![[!UICONTROL Erlebnisse nach Aktivitätskonversionen] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure6.png)

*Abbildung 6: Berichtsbereich mit dem Segment &quot;Treffer mit spezifischer Aktivität vom Typ Automatisches Targeting&quot;, das auf die [!UICONTROL Besuche] Metrik. Dieses Segment stellt sicher, dass nur Besuche, bei denen ein Benutzer tatsächlich mit der [!DNL Target] -Aktivität in den Bericht aufgenommen.*

## Ordnen Sie die Attribution zwischen ML-Modellschulung und der Zielmetrikgenerierung an.

Die A4T-Integration ermöglicht die [!UICONTROL Automatisches Targeting] ML-Modell, das verwendet werden soll *geschult* Verwendung derselben Konversionsereignisdaten, die [!DNL Adobe Analytics] verwendet *Leistungsberichte erstellen*. Es gibt jedoch bestimmte Annahmen, die bei der Auswertung dieser Daten bei der Schulung der ML-Modelle zugrunde gelegt werden müssen, die von den in der Berichterstellungsphase in [!DNL Adobe Analytics].

Insbesondere wird die [!DNL Adobe Target] ML-Modelle verwenden ein besuchsspezifisches Attributionsmodell. Das heißt, die ML-Modelle gehen davon aus, dass eine Konversion im selben Besuch wie eine Inhaltsanzeige für die Aktivität erfolgen muss, damit die Konversion der Entscheidung des ML-Modells &quot;zugeordnet&quot;wird. Dies ist erforderlich für [!DNL Target] Gewährleistung einer rechtzeitigen Ausbildung seiner Modelle; [!DNL Target] kann bis zu 30 Tage auf eine Konversion warten (das standardmäßige Attributionsfenster für Berichte in [!DNL Adobe Analytics]), bevor sie in die Trainings-Daten für ihre Modelle aufgenommen wird.

Daher der Unterschied zwischen der Attribution, die von der [!DNL Target] -Modelle (während des Trainings) im Vergleich zur Standardzuordnung, die bei der Abfrage von Daten (während der Berichterstellung) verwendet wird, können zu Diskrepanzen führen. Es kann sogar so aussehen, dass die ML-Modelle nur schlecht funktionieren, wenn das Problem in der Tat mit der Attribution liegt.

>[!TIP]
>
>Wenn die ML-Modelle für eine Metrik optimiert werden, die anders zugeordnet ist als die Metriken, die Sie in einem Bericht anzeigen, funktionieren die Modelle möglicherweise nicht erwartungsgemäß. Um dies zu vermeiden, stellen Sie sicher, dass die Zielmetriken in Ihrem Bericht die gleiche Attribution verwenden, die von der [!DNL Target] ML-Modelle.

So zeigen Sie Zielmetriken an, die dieselbe Attributionsmethodik aufweisen, die von der [!DNL Target] ML-Modelle, führen Sie die folgenden Schritte aus:

1. Bewegen Sie den Mauszeiger über das Zahnradsymbol der Zielmetrik:

   ![getriebe.png](assets/gearicon.png)

1. Scrollen Sie im resultierenden Menü zu **[!UICONTROL Dateneinstellungen]**.
1. Auswählen **[!UICONTROL Nicht standardmäßiges Attributionsmodell verwenden]** (falls noch nicht ausgewählt).

   ![non-defaultattributionmodel.png](assets/non-defaultattributionmodel.png)

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Auswählen **[!UICONTROL Modell]**: **[!UICONTROL Beitrag]** und **[!UICONTROL Lookback-Fenster]**: **[!UICONTROL Besuch]**.

   ![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)

1. Klicken Sie auf **[!UICONTROL Anwenden]**.

Diese Schritte stellen sicher, dass Ihr Bericht die Zielmetrik der Anzeige des Erlebnisses zuordnet, wenn das Zielmetrikereignis eintritt *beliebige Zeit* (&quot;Beitrag&quot;) im selben Besuch, bei dem ein Erlebnis angezeigt wurde.

## Endlicher Schritt: Erstellen Sie eine Konversionsrate, die die oben genannte Magie erfasst

Mit den Änderungen an der [!UICONTROL Besuch] und Zielmetriken in den vorherigen Abschnitten, der letzten Änderung, die Sie an Ihrer standardmäßigen A4T für [!UICONTROL Automatisches Targeting] im Berichtsbereich Konversionsraten zu erstellen, die das richtige Verhältnis (das einer Zielmetrik mit der richtigen Attribution) zu einer entsprechend gefilterten [!UICONTROL Besuche] Metrik.

Erstellen Sie dazu eine [!UICONTROL Berechnete Metrik] mit den folgenden Schritten:

1. Wählen Sie die **[!UICONTROL Komponenten > Metrik erstellen]** in der [!DNL Analysis Workspace] Symbolleiste.
1. Geben Sie eine **[!UICONTROL Titel]** für Ihre Metrik. Beispiel: &quot;Besuchskorrigierte Konversionsrate für Aktivität XXX&quot;.
1. Auswählen **[!UICONTROL Format]** = Prozent und **[!UICONTROL Dezimalstellen]** = 2.
1. Ziehen Sie die relevante Zielmetrik für Ihre Aktivität (z. B. [!UICONTROL Aktivitätskonversionen]) in die Definition ein und verwenden Sie das Zahnradsymbol für diese Zielmetrik, um das Attributionsmodell auf (Beitrag|Besuch) anzupassen, wie zuvor beschrieben.
1. Auswählen **[!UICONTROL Hinzufügen > Container]** oben rechts im **[!UICONTROL Definition]** Abschnitt.
1. Wählen Sie zwischen den beiden Behältern den Operator Division () aus.
1. Ziehen Sie das zuvor erstellte Segment mit dem Namen &quot;Treffer mit bestimmten [!UICONTROL Automatisches Targeting] Aktivität&quot;in diesem Tutorial [!DNL Auto-Target] Aktivität.
1. Ziehen Sie die **[!UICONTROL Besuche]** Metrik in den Segmentbehälter ein.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

Die vollständige Definition der berechneten Metrik wird hier angezeigt.

![Abbildung7.png](assets/Figure7.png)

*Abbildung 7: Die Metrikdefinition für die besuchskorrigierte und zuordnungskorrigierte Modellkonversionsrate. (Beachten Sie, dass diese Metrik von Ihrer Zielmetrik und -aktivität abhängt. Mit anderen Worten: Diese Metrikdefinition kann nicht über mehrere Aktivitäten hinweg wiederverwendet werden.)*

>[!IMPORTANT]
>
>Die [!UICONTROL Konversion] Die Metrik der Rate aus dem A4T-Bedienfeld ist nicht mit dem Konversionsereignis oder der Normalisierungsmetrik in der Tabelle verknüpft. Wenn Sie die in diesem Tutorial vorgeschlagenen Änderungen vornehmen, wird die [!UICONTROL Konversion] Die Rate passt sich nicht automatisch an die Änderungen an. Wenn Sie daher die Änderung an der Konversionsereigniszuordnung oder der Normalisierungsmetrik (oder beidem) vornehmen, müssen Sie sich als letzten Schritt merken, um auch die [!UICONTROL Konversion] -Rate, wie oben gezeigt.

## Zusammenfassung: Endgültige Probe [!DNL Analysis Workspace] Bereich für [!UICONTROL Automatisches Targeting] Berichte

Wenn Sie alle oben genannten Schritte in einem Bedienfeld kombinieren, zeigt die Abbildung unten eine vollständige Ansicht des empfohlenen Berichts für [!UICONTROL Automatisches Targeting] A4T-Aktivitäten. Dieser Bericht ist mit dem Bericht der [!DNL Target] ML-Modelle zur Optimierung Ihrer Zielmetrik. Der Bericht enthält alle in diesem Tutorial behandelten Nuancen und Empfehlungen. Dieser Bericht ähnelt auch den in der traditionellen [!DNL Target]-Berichterstattungsgesteuert [!UICONTROL Automatisches Targeting] Aktivitäten.

Klicken Sie auf , um das Bild zu erweitern.

![Abschließender A4T-Bericht in [!DNL Analysis Workspace]](assets/Figure8.png "A4T-Bericht in Analysis Workspace"){width="600" zoomable="yes"}

*Abbildung 8: Der endgültige A4T [!UICONTROL Automatisches Targeting] in [!DNL Adobe Analytics] [!DNL Workspace], die alle in den vorherigen Abschnitten dieses Tutorials beschriebenen Anpassungen an Metrikdefinitionen kombiniert.*
