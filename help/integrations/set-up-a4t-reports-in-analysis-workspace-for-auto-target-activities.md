---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] Tätigkeiten
description: Konfigurieren von A4T-Berichten in [!DNL Analysis Workspace] zum Abrufen der erwarteten Ergebnisse während der Ausführung [!UICONTROL Automatisches Targeting] Aktivitäten?
badgePremium: label="Premium" type="Positive" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en#premium" tooltip="See what's included in Target Premium."
badgeBeta: label="Beta" type="Informative"
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 58006a25-851e-43c8-b103-f143f72ee58d
source-git-commit: 12dc82a96a8df234d02dc56e9e5904571f2152ba
workflow-type: tm+mt
source-wordcount: '2636'
ht-degree: 1%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] activities

>[!NOTE]
>
>Diese Funktion ist derzeit als Betaversion verfügbar und steht allen [Target Premium](https://experienceleague.adobe.com/docs/target/using/introduction/intro.html?lang=en#premium){target=_blank} -Kunden in einer kommenden Version.

>[!IMPORTANT]
>
>Für [!UICONTROL Automatisches Targeting] Aktivitäten, müssen Sie die Berichterstellung unter [!DNL Analytics Workspace] und erstellen Sie manuell ein A4T-Bedienfeld.

Die [!UICONTROL Analytics for Target] (A4T)-Integration für [!DNL Auto-Target] Aktivitäten verwendet [!DNL Adobe Target]die Algorithmen des maschinellen Lernens (ML) verwenden, um basierend auf Profil, Verhalten und Kontext das beste Erlebnis für jeden Besucher auszuwählen, während gleichzeitig eine [!DNL Adobe Analytics] Zielmetrik.

Obwohl Rich-Analytics-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace], einige Änderungen an der Standardeinstellung **[!UICONTROL Analytics for Target]** -Bedienfeld zur korrekten Interpretation erforderlich [!DNL Auto-Target] Aktivitäten aufgrund von Unterschieden zwischen Experimentierungsaktivitäten (manuelle A/B- und automatische Zuordnung) und Personalisierungsaktivitäten ([!UICONTROL Automatisches Targeting]).

Dieses Tutorial führt Sie durch die empfohlenen Änderungen zur Analyse [!UICONTROL Automatisches Targeting] Aktivitäten in [!DNL Workspace], die auf den folgenden Schlüsselkonzepten basieren:

* Die **[!UICONTROL Kontrolle im Vergleich zu Zielgruppe]** -Dimension verwendet werden, um zwischen Kontrollerlebnissen und denen zu unterscheiden, die von der [!UICONTROL Automatisches Targeting] den ML-Algorithmus.
* Besuche sollten bei der Anzeige von Leistungsunterteilungen auf Erlebnisebene als Normalisierungsmetrik verwendet werden. Darüber hinaus [Die Standardzählmethodik von Adobe Analytics kann Besuche umfassen, bei denen der Benutzer keine Aktivitätsinhalte sieht](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html?lang=en#metrics), dieses Standardverhalten kann jedoch mithilfe eines entsprechend abgegrenzten Segments geändert werden (Details unten).
* Die Attribution mit Besuchs-Lookback - auch als &quot;Besuchs-Lookback-Fenster&quot;im vorgeschriebenen Attributionsmodell bezeichnet - wird von [!DNL Adobe Target]die ML-Modelle in ihren Trainings-Phasen und dasselbe (nicht standardmäßige) Attributionsmodell sollten bei der Unterteilung der Zielmetrik verwendet werden.

## Erstellen Sie A4T für [!UICONTROL Automatisches Targeting] Bedienfeld in [!DNL Workspace]

So erstellen Sie A4T für [!UICONTROL Automatisches Targeting] entweder mit der **[!UICONTROL Analytics for Target]** Bedienfeld in [!DNL Workspace], wie unten dargestellt, oder beginnen Sie mit einer Freiformtabelle. Wählen Sie dann die folgenden Optionen aus:

1. **[!UICONTROL Kontrollerlebnis]**: Sie können ein beliebiges Erlebnis auswählen. Sie werden diese Auswahl jedoch später überschreiben. Beachten Sie Folgendes: [!UICONTROL Automatisches Targeting] -Aktivitäten ist das Kontrollerlebnis tatsächlich eine Kontrollstrategie, die entweder a) zufällig unter allen Erlebnissen bereitgestellt wird oder b) ein einziges Erlebnis bereitstellt (diese Auswahl erfolgt zum Zeitpunkt der Aktivitätserstellung in [!DNL Adobe Target]). Selbst wenn Sie sich für die Wahl (b) entschieden haben - Ihre [!UICONTROL Automatisches Targeting] -Aktivität ein bestimmtes Erlebnis als Kontrollerlebnis bezeichnet hat. Sie sollten weiterhin den in diesem Tutorial zur Analyse von A4T für [!UICONTROL Automatisches Targeting] Aktivitäten.
2. **[!UICONTROL Normalisierungsmetrik]**: Wählen Sie Besuche aus.
3. **[!UICONTROL Erfolgsmetriken]**: Obwohl Sie eine oder mehrere Metriken auswählen können, für die ein Bericht erstellt werden soll, sollten Sie im Allgemeinen Berichte zu derselben Metrik anzeigen, die bei der Aktivitätserstellung in [!DNL Target].

![Abbildung1.png](assets/Figure1.png)
*Abbildung 1: [!UICONTROL Analytics for Target] Bedienfeldeinstellungen für [!UICONTROL Automatisches Targeting] Aktivitäten.*

>[!NOTE]
>
>So richten Sie [!UICONTROL Analytics for Target] Bereich für [!UICONTROL Automatisches Targeting] Aktivitäten, beliebiges Kontrollerlebnis auswählen, [!UICONTROL Besuche] als Normalisierungsmetrik verwenden und dieselbe Zielmetrik auswählen, die während der [!DNL Target] Aktivitätserstellung.

## Verwenden Sie die [!UICONTROL Kontrolle vs. Targeting] Dimension zum Vergleich [!DNL Target] ML-Modell für Ihr Steuerelement zusammenführen

Das standardmäßige A4T-Bedienfeld wurde für klassische (manuelle) A/B-Tests oder [!UICONTROL Automatische Zuordnung] Aktivitäten, bei denen das Ziel darin besteht, die Leistung einzelner Erlebnisse mit dem Kontrollerlebnis zu vergleichen. In [!UICONTROL Automatisches Targeting] -Aktivitäten, sollte jedoch der erste Auftragsvergleich zwischen der Kontrollgruppe *strategy* und die Zielgruppe *strategy* (d. h. die Ermittlung der Steigerung der Gesamtleistung der [!UICONTROL Automatisches Targeting] ML-Modell über die Kontrollstrategie).

Verwenden Sie für diesen Vergleich die **[!UICONTROL Kontrolle vs. Targeting (Analytics für Target)]** Dimension. Ziehen und ablegen , um die **[!UICONTROL Target-Erlebnisse]** -Dimension im standardmäßigen A4T-Bericht.

Beachten Sie, dass diese Ersetzung die standardmäßigen Steigerungs- und Konfidenzberechnungen im A4T-Bedienfeld ungültig macht. Um Verwirrung zu vermeiden, können Sie diese Metriken aus dem Standardbereich entfernen und den folgenden Bericht beibehalten:

![Abbildung2.png](assets/Figure2.png)

*Abbildung 2: Der empfohlene Ausgangsbericht für [!DNL Auto-Target] Aktivitäten. Dieser Bericht wurde so konfiguriert, dass er zielgerichteten Traffic (bereitgestellt vom Ensemble ML-Modell) mit Ihrem Control-Traffic vergleicht.*

>[!NOTE]
>
>Derzeit sind die Steigerungs- und Konfidenzzahlen nicht für [!UICONTROL Kontrolle im Vergleich zu Zielgruppe] Dimensionen für A4T-Berichte für [!UICONTROL Automatisches Targeting]. Bis die Unterstützung hinzugefügt ist, können Steigerung und Konfidenz manuell berechnet werden, indem die [Vertrauensrechner](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx?lang=en).

## Aufschlüsselungen von Metriken auf Erlebnisebene hinzufügen

Um weitere Einblicke in die Leistung des ML-Ensemble-Modells zu erhalten, können Sie die Aufschlüsselungen auf Erlebnisebene der **[!UICONTROL Kontrolle im Vergleich zu Zielgruppe]** Dimension. In [!DNL Workspace], ziehen Sie die **[!UICONTROL Target-Erlebnisse]** in den Bericht ein und unterteilen dann jede der Dimensionen Kontrolle und Zielgruppe separat.

![Abbildung3.png](assets/Figure3.png)
*Abbildung 3: Aufschlüsseln der Zielgruppendimension nach Target-Erlebnissen*

Ein Beispiel für den resultierenden Bericht finden Sie hier.

![Abbildung4.png](assets/Figure4.png)
*Abbildung 4: Ein Standard [!UICONTROL Automatisches Targeting] mit Aufschlüsselungen auf Erlebnisebene. Beachten Sie, dass Ihre Zielmetrik möglicherweise anders ist und Ihre Kontrollstrategie über ein einziges Erlebnis verfügen kann.*

>[!TIP]
>
>In [!DNL Workspace]klicken Sie auf das Zahnradsymbol, um die Prozentsätze im [!UICONTROL Konversionsrate] um den Fokus auf die Erlebniskonversionsraten zu legen. Beachten Sie, dass die Konversionsraten dann als Dezimalzahlen formatiert werden, sie jedoch entsprechend als Prozentsätze interpretiert werden.

## Warum &quot;Besuche&quot;die richtige Normalisierungsmetrik für [!UICONTROL Automatisches Targeting] activities

Bei der Analyse einer [!UICONTROL Automatisches Targeting] Aktivität, immer wählen [!UICONTROL Besuche] als standardmäßige Normalisierungsmetrik. [!UICONTROL Automatisches Targeting] Personalisierung wählt ein Erlebnis für einen Besucher einmal pro Besuch aus (formell einmal pro Besuch [!DNL Adobe Target] Sitzung), was bedeutet, dass sich das einem Benutzer angezeigte Erlebnis bei jedem einzelnen Besuch ändern kann. Wenn Sie [!UICONTROL Unique Visitors] als Normalisierungsmetrik verwendet wird, würde die Tatsache, dass einem einzelnen Benutzer (über verschiedene Besuche hinweg) am Ende mehrere Erlebnisse angezeigt werden, zu verwirrenden Konversionsraten führen.

Ein einfaches Beispiel zeigt diesen Punkt: betrachten ein Szenario, in dem zwei Besucher an einer Kampagne teilnehmen, die nur über zwei Erlebnisse verfügt. Der erste Besucher besucht zweimal. Sie werden Erlebnis A beim ersten Besuch, Erlebnis B beim zweiten Besuch zugewiesen (da sich ihr Profilstatus bei diesem zweiten Besuch ändert). Nach dem zweiten Besuch wandelt der Besucher durch eine Bestellung um. Die Konversion wird dem zuletzt angezeigten Erlebnis (Erlebnis B) zugeordnet. Der zweite Besucher besucht auch zweimal. Erlebnis B wird beide Male angezeigt, jedoch nie konvertiert.

Vergleichen wir Berichte auf Besucher- und Besuchsebene:

| Erlebnis | Unique Visitors | Besuche | Konversionen | Besuchernorm. Siehe Rate | Besuchsnorm. Siehe Rate |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0% | 0% |
| B | 2 | 3 | 1 | 50% | 33.3% |
| Gesamt | 2 | 4 | 1 | 50% | 25 % |

*Tabelle 1: Beispiel für den Vergleich von besuchernormalisierten und besuchsnormalisierten Berichten für ein Szenario, in dem Entscheidungen an einen Besuch gebunden sind (und nicht an Besucher, wie bei regulären A/B-Tests). Besuchernormalisierte Metriken verwirren in diesem Szenario.*

Wie in der Tabelle gezeigt, besteht eine eindeutige Unstimmigkeit zwischen Zahlen auf Besucherebene. Obwohl es insgesamt zwei Unique Visitors gibt, handelt es sich hierbei nicht um eine Summe einzelner Unique Visitors für jedes Erlebnis. Auch wenn die Konversionsrate auf Besucherebene nicht unbedingt falsch ist, ergeben Konversionsraten auf Besuchsebene beim Vergleich einzelner Erlebnisse wohl deutlich mehr Sinn. Formell entspricht die Analyseeinheit (&quot;Besuche&quot;) der Entscheidungs-Treue, was bedeutet, dass Aufschlüsselungen von Metriken auf Erlebnisebene hinzugefügt und verglichen werden können.

## Filtern nach tatsächlichen Besuchen der Aktivität

Die [!DNL Adobe Analytics] Standardzählmethodik für Besuche bei einer [!DNL Target] -Aktivität kann Besuche umfassen, bei denen der Benutzer nicht mit der [!DNL Target] Aktivität. Dies ist auf die [!DNL Target] Aktivitätszuweisungen werden im [!DNL Analytics] Besucherkontext. Die Anzahl der Besuche bei der [!DNL Target] Die Aktivität kann in manchen Fällen überhöht sein, was zu einem Rückgang der Konversionsraten führt.

Wenn Sie Berichte zu Besuchen bevorzugen, bei denen der Benutzer tatsächlich mit der [!UICONTROL Automatisches Targeting] -Aktivität (entweder durch Einstieg in die Aktivität, ein Anzeige-/Besuchsereignis oder eine Konversion) können Sie:

1. Erstellen Sie ein bestimmtes Segment, das Treffer aus dem [!DNL Target] die betreffende Aktivität und
1. Filtern Sie die [!UICONTROL Besuche] Metrik mithilfe dieses Segments.

**So erstellen Sie das Segment:**

1. Wählen Sie die **[!UICONTROL Komponenten > Segment erstellen]** in der [!DNL Workspace] Symbolleiste.
2. Geben Sie einen **[!UICONTROL Titel]** für Ihr Segment. Im unten gezeigten Beispiel heißt das Segment [!DNL "Hit with specific Auto-Target activity"].
3. Ziehen Sie die **[!UICONTROL Target Activities]** Dimension zum Segment **[!UICONTROL Definition]** Abschnitt.
4. Verwenden Sie die **[!UICONTROL gleich]** Operator.
5. Suchen Sie nach Ihren spezifischen [!DNL Target] Aktivität.
6. Wählen Sie das Zahnradsymbol aus und klicken Sie dann auf **[!UICONTROL Attributionsmodell > Instanz]** wie in der folgenden Abbildung dargestellt.
7. Klicken Sie auf **[!UICONTROL Speichern]**.

![Abbildung 5.png](assets/Figure5.png)
*Abbildung 5: Verwenden Sie ein Segment wie das hier angezeigte, um die [!UICONTROL Besuche] Metrik in Ihrem A4T für [!UICONTROL Automatisches Targeting] Bericht*

Nachdem das Segment erstellt wurde, verwenden Sie es zum Filtern der [!UICONTROL Besuche] Metrik, also die [!UICONTROL Besuche] Metrik umfasst nur Besuche, bei denen der Benutzer mit der [!DNL Target] Aktivität.

**Filter [!UICONTROL Besuche] mithilfe dieses Segments:**

1. Ziehen Sie das neu erstellte Segment aus der Komponenten-Symbolleiste und bewegen Sie den Mauszeiger über die Basis der **[!UICONTROL Besuche]** Metrikbezeichnung bis zu einem blauen **[!UICONTROL Filtern nach]** wird angezeigt.
2. Lassen Sie das Segment frei. Der Filter wird auf diese Metrik angewendet.

Das endgültige Bedienfeld wird wie folgt angezeigt.

![Abbildung6.png](assets/Figure6.png)
*Abbildung 6: Berichtsbereich mit dem Segment &quot;Treffer mit spezifischer Aktivität vom Typ Automatisches Targeting&quot;, das auf die [!UICONTROL Besuche] Metrik. Dadurch werden nur Besuche sichergestellt, bei denen ein Benutzer tatsächlich mit der [!DNL Target] -Aktivität in den Bericht aufgenommen.*

## Stellen Sie sicher, dass die Zielmetrik und Attribution mit Ihrem Optimierungskriterium übereinstimmen.

Die A4T-Integration ermöglicht die [!UICONTROL Automatisches Targeting] ML-Modell, das verwendet werden soll *geschult* Verwendung derselben Konversionsereignisdaten, die [!DNL Adobe Analytics] verwendet *Leistungsberichte erstellen*. Es gibt jedoch bestimmte Annahmen, die bei der Auswertung dieser Daten bei der Schulung der ML-Modelle zugrunde gelegt werden müssen, die von den in der Berichterstattungsphase in [!DNL Adobe Analytics].

Insbesondere wird die [!DNL Adobe Target] ML-Modelle verwenden ein besuchsspezifisches Attributionsmodell. Das heißt, sie gehen davon aus, dass eine Konversion im selben Besuch wie eine Inhaltsanzeige für die Aktivität erfolgen muss, damit die Konversion der Entscheidung des ML-Modells &quot;zugeordnet&quot;wird. Dies ist erforderlich für [!DNL Target] Gewährleistung einer rechtzeitigen Ausbildung seiner Modelle; [!DNL Target] kann bis zu 30 Tage auf eine Konversion warten (das standardmäßige Attributionsfenster für Berichte in [!DNL Adobe Analytics]), bevor sie in die Trainings-Daten für ihre Modelle aufgenommen wird.

Daher der Unterschied zwischen der Attribution, die von der [!DNL Target] -Modelle (während des Trainings) im Vergleich zur Standardzuordnung, die bei der Abfrage von Daten (während der Berichterstellung) verwendet wird, können zu Diskrepanzen führen. Es kann sogar vorkommen, dass die ML-Modelle nur schlecht funktionieren, wenn das Problem in der Tat mit der Attribution liegt.

>[!TIP]
>
>Wenn die ML-Modelle für eine Metrik optimiert werden, die anders zugeordnet ist als die Metriken, die Sie in einem Bericht anzeigen, können die Modelle nicht erwartungsgemäß funktionieren! Um dies zu vermeiden, stellen Sie sicher, dass die Zielmetriken in Ihrem Bericht dieselbe Metrikdefinition und -zuordnung verwenden, die von den ML-Modellen von Target verwendet werden.

Die genaue Metrikdefinition und die Attributionseinstellungen hängen von der [Optimierungskriterium](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#supported) die Sie bei der Erstellung der Aktivität angegeben haben.

### Target-definierte Konversionen oder Analytics-Metriken mit *Metrikwert pro Besuch maximieren*

Wenn es sich bei der Metrik um eine Target-Konversion oder eine Analytics-Metrik mit **Metrikwert pro Besuch maximieren**, ermöglicht die Zielmetrikdefinition, dass mehrere Konversionsereignisse im selben Besuch auftreten.
Gehen Sie wie folgt vor, um Zielmetriken anzuzeigen, die dieselbe Attributionsmethodik aufweisen, die von den ML-Modellen von Adobe Target verwendet wird:

![getriebe.png](assets/gearicon.png)

1. Scrollen Sie im resultierenden Menü zu **[!UICONTROL Dateneinstellungen]**.
1. Auswählen **[!UICONTROL Nicht standardmäßiges Attributionsmodell verwenden]** (sofern nicht bereits ausgewählt):

![non-defaultattributionmodel.png](assets/non-defaultattributionmodel.png)

1. Klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Auswählen **[!UICONTROL Modell]**: **[!UICONTROL Beitrag]** und **[!UICONTROL Lookback-Fenster]**: **[!UICONTROL Besuch]**.

![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)

1. Klicken Sie auf **[!UICONTROL Anwenden]**.

Diese Schritte stellen sicher, dass Ihr Bericht die Zielmetrik der Anzeige des Erlebnisses zuordnet, wenn das Zielmetrikereignis eintritt *beliebige Zeit* (&quot;Beitrag&quot;) im selben Besuch, bei dem ein Erlebnis angezeigt wurde.

### Analytics-Metriken mit *Konversionsraten einzelner Besuche*

**Definieren des Besuchs mit positivem Metriksegment**

Im Szenario, in dem Sie ausgewählt haben *Maximieren der Konversionsrate individueller Besuche* als Optimierungskriterium verwenden, ist die korrekte Definition der Konversionsrate der Anteil der Besuche, bei denen der Metrikwert positiv ist. Dies kann erreicht werden, indem ein Segment erstellt wird, das nach Besuchen mit einem positiven Wert der Metrik filtert und dann die Besuchsmetrik gefiltert wird.


1. Wählen Sie wie zuvor die **[!UICONTROL Komponenten > Segment erstellen]** in der Workspace-Symbolleiste.
2. Geben Sie einen **[!UICONTROL Titel]** für Ihr Segment. Im unten gezeigten Beispiel heißt das Segment [!DNL "Visits with an order"].
3. Ziehen Sie die Basismetrik, die Sie in Ihrem Optimierungsziel verwendet haben, in das Segment . Im folgenden Beispiel verwenden wir die **Bestellungen** Metrik, sodass die Konversionsrate den Anteil der Besuche misst, bei denen eine Bestellung aufgezeichnet wird.
4. Wählen Sie oben links im Segmentdefinitionscontainer die Option **[!UICONTROL Einschließen]** **Besuch**.
5. Verwenden Sie die **[!UICONTROL größer als]** und setzen Sie den Wert auf 0 (d. h. dieses Segment umfasst Besuche, bei denen die Bestellungsmetrik positiv ist).
6. Klicken Sie auf **[!UICONTROL Speichern]**.

![Abbildung7.png](assets/Figure7.png)
*Abbildung 7: Die Segmentdefinition filtert nach Besuchen mit einer positiven Reihenfolge. Je nach Optimierungsmetrik Ihrer Aktivität müssen Sie Bestellungen durch eine entsprechende Metrik ersetzen*

**Wenden Sie dies auf Besuche in der Aktivitätsgefilterten Metrik an**

Dieses Segment kann jetzt verwendet werden, um nach Besuchen mit einer positiven Anzahl von Bestellungen zu filtern und wo ein Treffer für die [!DNL Auto-Target]Aktivität. Das Verfahren zum Filtern einer Metrik ähnelt dem zuvor. Nach Anwendung des neuen Segments auf die bereits gefilterte Besuchsmetrik sollte das Berichtsbedienfeld wie in Abbildung 8 dargestellt aussehen

![Abbildung8.png](assets/Figure8.png)
*Abbildung 8: Das Berichtbedienfeld mit der korrekten Konversionsmetrik für Unique Visits - d. h. die Anzahl der Besuche, bei denen ein Treffer aus der Aktivität aufgezeichnet wurde und bei denen die Konversionsmetrik (Bestellungen in diesem Beispiel) ungleich null war.*


## Endlicher Schritt: Erstellen Sie eine Konversionsrate, die die oben genannte Magie erfasst

Mit den Änderungen an der [!UICONTROL Besuch] und Zielmetriken in den vorherigen Abschnitten, der letzten Änderung, die Sie an Ihrer standardmäßigen A4T für [!UICONTROL Automatisches Targeting] im Berichtsbereich Konversionsraten zu erstellen, die das richtige Verhältnis - das einer Zielmetrik mit der richtigen Attribution - zu einer entsprechend gefilterten [!UICONTROL Besuche] Metrik.

Erstellen Sie dazu eine berechnete Metrik mithilfe der folgenden Schritte:

1. Wählen Sie die **[!UICONTROL Komponenten > Metrik erstellen]** in der [!DNL Workspace] Symbolleiste.
1. Geben Sie einen **[!UICONTROL Titel]** für Ihre Metrik. Beispiel: &quot;Besuchskorrigierte Konversionsrate für Aktivität XXX&quot;.
1. Auswählen **[!UICONTROL Format]** = Prozent und **[!UICONTROL Dezimalstellen]** = 2.
1. Ziehen Sie die relevante Zielmetrik für Ihre Aktivität (z. B. [!UICONTROL Aktivitätskonversionen]) in die Definition ein und verwenden Sie das Zahnradsymbol für diese Zielmetrik, um das Attributionsmodell auf (Beitrag|Besuch) anzupassen, wie zuvor beschrieben.
1. Auswählen **[!UICONTROL Hinzufügen > Container]** oben rechts im **[!UICONTROL Definition]** Abschnitt.
1. Wählen Sie zwischen den beiden Behältern den Operator Division () aus.
1. Ziehen Sie das zuvor erstellte Segment mit dem Namen &quot;Treffer mit bestimmten [!UICONTROL Automatisches Targeting] -Aktivität&quot;in diesem Tutorial - für diese spezifische [!DNL Auto-Target] Aktivität.
1. Ziehen Sie die **[!UICONTROL Besuche]** Metrik in den Segmentbehälter ein.
1. Klicken Sie auf **[!UICONTROL Speichern]**.

>[!TIP]
>
> Sie können diese Metrik auch mithilfe der [Funktionen für schnelle berechnete Metriken](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html?lang=en).

Die vollständige Definition der berechneten Metrik wird hier angezeigt.

![Abbildung9.png](assets/Figure9.png)
*Abbildung 9: Die Metrikdefinition für die besuchs- und zuordnungskorrigierte Modellkonversionsrate. (Beachten Sie, dass diese Metrik von Ihrer Zielmetrik und -aktivität abhängt. Mit anderen Worten: Diese Metrikdefinition kann nicht über mehrere Aktivitäten hinweg wiederverwendet werden.)*

>[!IMPORTANT]
>
>Die Metrik Konversionsrate aus dem A4T-Bedienfeld ist nicht mit dem Konversionsereignis oder der Normalisierungsmetrik in der Tabelle verknüpft. Wenn Sie die in diesem Tutorial vorgeschlagenen Änderungen vornehmen, passt sich die Konversionsrate nicht automatisch an die Änderungen an. Wenn Sie daher die Änderung an einer (oder beiden) der Konversionsereigniszuordnung und der Normalisierungsmetrik vornehmen, müssen Sie sich als letzten Schritt merken, um auch die Konversionsrate zu ändern, wie oben gezeigt.

## Zusammenfassung: Endgültige Probe [!DNL Workspace] Bereich für [!UICONTROL Automatisches Targeting] Berichte

Wenn Sie alle oben genannten Schritte in einem Bedienfeld kombinieren, zeigt die Abbildung unten eine vollständige Ansicht des empfohlenen Berichts für [!UICONTROL Automatisches Targeting] A4T-Aktivitäten. Dieser Bericht ist mit dem Bericht der [!DNL Target] ML-Modelle zur Optimierung Ihrer Zielmetrik verwenden, und sie enthält alle in diesem Tutorial behandelten Nuancen und Empfehlungen. Dieser Bericht ähnelt auch den in der traditionellen [!DNL Target]-Berichterstattungsgesteuert [!UICONTROL Automatisches Targeting] Aktivitäten.

![Abbildung 10.png](assets/Figure10.png)
*Abbildung 10: Der endgültige A4T [!UICONTROL Automatisches Targeting] in [!DNL Adobe Analytics] [!DNL Workspace], die alle in den vorherigen Abschnitten dieses Dokuments beschriebenen Anpassungen an Metrikdefinitionen kombiniert.*
