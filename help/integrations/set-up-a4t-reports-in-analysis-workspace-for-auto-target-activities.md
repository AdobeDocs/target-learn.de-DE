---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] Aktivitäten
description: Wie konfiguriere ich A4T-Berichte in [!DNL Analysis Workspace] für die erwarteten Ergebnisse bei der Ausführung von [!UICONTROL Auto-Target] -Aktivitäten?
badgePremium: label="Premium" type="Positive" url="https://experienceleague.adobe.com/docs/target/using/introduction/intro.html#premium newtab=true" tooltip="Erfahren Sie, was in Target Premium enthalten ist."
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
thumbnail: null
kt: null
exl-id: 58006a25-851e-43c8-b103-f143f72ee58d
source-git-commit: 78e5b5f7fa8f4c1a08c06c6d2b0e1a5242cd464c
workflow-type: tm+mt
source-wordcount: '2430'
ht-degree: 1%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Target] -Aktivitäten

>[!IMPORTANT]
>
>Bei [!UICONTROL Auto-Target] -Aktivitäten müssen Sie die Berichterstellung in [!DNL Analytics Workspace] überprüfen und manuell ein A4T-Bedienfeld erstellen.

Die Integration von [!UICONTROL Analytics for Target] (A4T) für [!DNL Auto-Target] -Aktivitäten verwendet die Algorithmen des maschinellen Lernens (ML) des [!DNL Adobe Target]-Ensembles, um das beste Erlebnis für jeden Besucher basierend auf seinem Profil, Verhalten und Kontext auszuwählen, während eine Zielmetrik vom Typ [!DNL Adobe Analytics] verwendet wird.

Obwohl Rich-Analyse-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace] verfügbar sind, sind einige Änderungen am standardmäßigen Bedienfeld **[!UICONTROL Analytics for Target]** erforderlich, um [!DNL Auto-Target] -Aktivitäten korrekt zu interpretieren. Dies liegt an Unterschieden zwischen Experimentierungsaktivitäten (manuell [!UICONTROL A/B Test] und [!UICONTROL Auto-Allocate]) und Personalisierungsaktivitäten ([!UICONTROL [!UICONTROL Auto-Target]]).

Dieses Tutorial führt Sie durch die empfohlenen Änderungen zur Analyse von [!UICONTROL Auto-Target] -Aktivitäten in [!DNL Analysis Workspace], die auf den folgenden Schlüsselkonzepten basieren:

* Die Dimension **[!UICONTROL Control vs Targeted]** kann verwendet werden, um zwischen [!UICONTROL Control] Erlebnissen und Erlebnissen zu unterscheiden, die vom ML-Ensemble-Algorithmus [!UICONTROL Auto-Target] bereitgestellt werden.
* Besuche sollten bei der Anzeige von Leistungsunterteilungen auf Erlebnisebene als Normalisierungsmetrik verwendet werden. Darüber hinaus kann die Standardzählmethodik von [Adobe Analytics Besuche umfassen, bei denen der Benutzer tatsächlich keinen Aktivitätsinhalt anzeigt](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-faq/a4t-faq-viewing-reports.html#metrics){target=_blank}. Dieses Standardverhalten kann jedoch durch die Verwendung eines entsprechend umfangreichen Segments (Details unten) geändert werden.
* Die Attribution mit Besuchs-Lookback-Scoped, die auch als &quot;Besuchs-Lookback-Fenster&quot;auf dem vorgeschriebenen Attributionsmodell bezeichnet wird, wird von den [!DNL Adobe Target] ML-Modellen während ihrer Trainings-Phasen verwendet und dasselbe (nicht standardmäßige) Attributionsmodell sollte bei der Aufschlüsselung der Zielmetrik verwendet werden.

## Erstellen des A4T-Bedienfelds für [!UICONTROL Auto-Target] in [!DNL Analysis Workspace]

Um einen A4T-Bericht für [!UICONTROL Auto-Target] zu erstellen, beginnen Sie entweder mit dem Bedienfeld **[!UICONTROL Analytics for Target]** in [!DNL Analysis Workspace] (wie unten dargestellt) oder beginnen Sie mit einer Freiformtabelle. Wählen Sie dann die folgenden Optionen aus:

1. **[!UICONTROL Control Experience]**: Sie können ein beliebiges Erlebnis auswählen. Diese Auswahl wird jedoch später überschrieben. Beachten Sie, dass das Kontrollerlebnis bei [!UICONTROL Auto-Target] -Aktivitäten wirklich eine Kontrollstrategie ist, die entweder a) zufällig unter allen Erlebnissen bereitgestellt wird oder b) ein einziges Erlebnis bereitstellt (diese Auswahl erfolgt zum Zeitpunkt der Aktivitätserstellung in [!DNL Adobe Target]). Selbst wenn Sie sich für Auswahl (b) entschieden haben, hat Ihre [!UICONTROL Auto-Target] -Aktivität ein bestimmtes Erlebnis als Kontrollelement ausgewiesen. Sie sollten weiterhin den in diesem Tutorial zur Analyse von A4T für [!UICONTROL Auto-Target] -Aktivitäten beschriebenen Ansatz verfolgen.
2. **[!UICONTROL Normalizing Metric]**: Wählen Sie [!UICONTROL Visits] aus.
3. **[!UICONTROL Success Metrics]**: Obwohl Sie beliebige Metriken auswählen können, für die ein Bericht erstellt werden soll, sollten Sie im Allgemeinen Berichte zu derselben Metrik anzeigen, die bei der Aktivitätserstellung in [!DNL Target] zur Optimierung ausgewählt wurde.

   ![[!UICONTROL Analytics for Target] Bedienfeld-Setup für [!UICONTROL Auto-Target] Aktivitäten.](assets/Figure1.png)

   *Abbildung 1: [!UICONTROL Analytics for Target] Bedienfeld-Setup für [!UICONTROL Auto-Target] Aktivitäten.*

>[!TIP]
>
>Um Ihr [!UICONTROL Analytics for Target] -Bedienfeld für [!UICONTROL Auto-Target] -Aktivitäten einzurichten, wählen Sie ein Kontrollerlebnis aus, wählen Sie [!UICONTROL Visits] als Normalisierungsmetrik und wählen Sie dieselbe Zielmetrik aus, die bei der Erstellung von [!DNL Target] -Aktivitäten zur Optimierung ausgewählt wurde.

## Verwenden Sie die Dimension &quot;[!UICONTROL Control vs.Targeted]&quot;, um das ML-Ensemble-Modell [!DNL Target] mit Ihrer Kontrolle zu vergleichen.

Das standardmäßige A4T-Bedienfeld wurde für klassische (manuelle) [!UICONTROL A/B Test] - oder [!UICONTROL Auto-Allocate] -Aktivitäten entwickelt, bei denen das Ziel darin besteht, die Leistung einzelner Erlebnisse mit dem Kontrollerlebnis zu vergleichen. In [!UICONTROL Auto-Target] -Aktivitäten sollte der Vergleich der ersten Reihenfolge jedoch zwischen der Kontrolle *strategy* und der gezielten *strategy* erfolgen. Anders ausgedrückt: Bestimmung der Steigerung der Gesamtleistung des ML-Modells [!UICONTROL Auto-Target] im Vergleich zur Kontrollstrategie.

Verwenden Sie für diesen Vergleich die Dimension &quot;**[!UICONTROL Control vs Targeted (Analytics for Target)]**&quot;. Ziehen Sie per Drag-and-Drop die Dimension **[!UICONTROL Target Experiences]** in den standardmäßigen A4T-Bericht.

Beachten Sie, dass diese Ersetzung die standardmäßigen [!UICONTROL Lift and Confidence] -Berechnungen im A4T-Bedienfeld ungültig macht. Um Verwirrung zu vermeiden, können Sie diese Metriken aus dem Standardbereich entfernen und den folgenden Bericht beibehalten:

![[!UICONTROL Experiences by Activity Conversions] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure2.png)

*Abbildung 2: Der empfohlene Ausgangsbericht für [!DNL Auto-Target] -Aktivitäten. Dieser Bericht wurde so konfiguriert, dass zielgerichteter Traffic (bereitgestellt vom Ensemble ML-Modell) mit Ihrem Kontroll-Traffic verglichen wird.*

>[!NOTE]
>
>Derzeit sind [!UICONTROL Lift and Confidence] Zahlen nicht für [!UICONTROL Control vs Targeted] Dimensionen für A4T-Berichte für [!UICONTROL Auto-Target] verfügbar. Bis die Unterstützung hinzugefügt ist, kann [!UICONTROL Lift and Confidence] manuell berechnet werden, indem der [Vertrauensrechner](https://experienceleague.adobe.com/docs/target/assets/complete_confidence_calculator.xlsx) heruntergeladen wird.

## Aufschlüsselungen von Metriken auf Erlebnisebene hinzufügen

Um weitere Einblicke in die Leistung des Ensemble-ML-Modells zu erhalten, können Sie Aufschlüsselungen auf Erlebnisebene der Dimension **[!UICONTROL Control vs Targeted]** untersuchen. Ziehen Sie in [!DNL Analysis Workspace] die Dimension **[!UICONTROL Target Experiences]** in Ihren Bericht und unterteilen Sie dann jede Kontroll- und Zielgruppendimension separat.

![[!UICONTROL Experiences by Activity Conversions] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure3.png)

*Abbildung 3: Aufschlüsseln der Zielgruppendimension nach Target-Erlebnissen*

Ein Beispiel für den resultierenden Bericht finden Sie hier.

![[!UICONTROL Experiences by Activity Conversions] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure4.png)

*Abbildung 4: Ein standardmäßiger [!UICONTROL Auto-Target] Bericht mit Aufschlüsselungen auf Erlebnisebene. Beachten Sie, dass Ihre Zielmetrik möglicherweise anders ist und Ihre Kontrollstrategie über ein einziges Erlebnis verfügen kann.*

>[!TIP]
>
>Klicken Sie in [!DNL Analysis Workspace] auf das Zahnradsymbol, um die Prozentsätze in der Spalte [!UICONTROL Conversion Rate] auszublenden, damit der Fokus weiterhin auf die Erlebniskonversionsraten gelegt wird. Die Konversionsraten werden dann als Dezimalzahlen formatiert, aber entsprechend als Prozentsätze interpretiert.

## Warum &quot;[!UICONTROL Visits]&quot; die richtige Normalisierungsmetrik für [!UICONTROL Auto-Target] -Aktivitäten ist

Wählen Sie bei der Analyse einer [!UICONTROL Auto-Target] -Aktivität immer [!UICONTROL Visits] als standardmäßige Normalisierungsmetrik. Durch die Personalisierung von [!UICONTROL Auto-Target] wird ein Erlebnis für einen Besucher einmal pro Besuch (formell einmal pro [!DNL Target] Sitzung) ausgewählt. Dies bedeutet, dass sich das einem Besucher angezeigte Erlebnis bei jedem einzelnen Besuch ändern kann. Wenn Sie daher [!UICONTROL Unique Visitors] als Normalisierungsmetrik verwenden, würde die Tatsache, dass einem einzelnen Benutzer (über verschiedene Besuche hinweg) am Ende mehrere Erlebnisse angezeigt werden, zu verwirrenden Konversionsraten führen.

Ein einfaches Beispiel zeigt diesen Punkt: Nehmen wir ein Szenario, in dem zwei Besucher an einer Kampagne teilnehmen, die nur über zwei Erlebnisse verfügt. Der erste Besucher besucht zweimal. Sie werden Erlebnis A beim ersten Besuch, Erlebnis B beim zweiten Besuch zugewiesen (da sich ihr Profilstatus bei diesem zweiten Besuch ändert). Nach dem zweiten Besuch wandelt der Besucher durch eine Bestellung um. Die Konversion wird dem zuletzt angezeigten Erlebnis (Erlebnis B) zugeordnet. Der zweite Besucher besucht auch zweimal. Erlebnis B wird beide Male angezeigt, jedoch nie konvertiert.

Vergleichen wir Berichte auf Besucher- und Besuchsebene:

| Erlebnis | Unique Visitors | Besuche | Konversionen | Besuchernormalisierte Konversionsrate | Besuchsnormalisierte Konversionsrate |
| --- | --- | --- | --- | --- | --- |
| A | 1 | 1 | - | 0 % | 0 % |
| B | 2 | 3 | 1 | 50% | 33,3 % |
| Gesamt | 2 | 4 | 1 | 50% | 25 % |

*Tabelle 1: Beispiel für den Vergleich von besuchernormalisierten und besuchsnormalisierten Berichten für ein Szenario, in dem Entscheidungen an einen Besuch gebunden sind (und nicht an Besucher, wie bei regulären A/B-Tests). Besuchernormalisierte Metriken verwirren in diesem Szenario.*

Wie in der Tabelle gezeigt, besteht eine eindeutige Unstimmigkeit zwischen Zahlen auf Besucherebene. Obwohl es insgesamt zwei Unique Visitors gibt, handelt es sich hierbei nicht um eine Summe einzelner Unique Visitors für jedes Erlebnis. Auch wenn die Konversionsrate auf Besucherebene nicht unbedingt falsch ist, ergeben Konversionsraten auf Besuchsebene beim Vergleich einzelner Erlebnisse wohl deutlich mehr Sinn. Formell entspricht die Analyseeinheit (&quot;Besuche&quot;) der Entscheidungs-Treue, was bedeutet, dass Aufschlüsselungen von Metriken auf Erlebnisebene hinzugefügt und verglichen werden können.

## Filtern nach tatsächlichen Besuchen der Aktivität

Die Standardzählmethodik von [!DNL Adobe Analytics] für Besuche einer [!DNL Target] -Aktivität kann Besuche umfassen, bei denen der Benutzer nicht mit der [!DNL Target] -Aktivität interagiert hat. Dies liegt daran, wie [!DNL Target]-Aktivitätszuweisungen im Besucherkontext von [!DNL Analytics] beibehalten werden. Daher kann die Anzahl der Besuche bei der [!DNL Target] -Aktivität manchmal zu hoch sein, was zu einem Rückgang der Konversionsraten führt.

Wenn Sie Berichte zu Besuchen bevorzugen, bei denen der Benutzer tatsächlich mit der [!UICONTROL Auto-Target] -Aktivität interagiert hat (entweder durch Einstieg in die Aktivität, ein Anzeige- oder Besuchsereignis oder eine Konversion), können Sie Folgendes tun:

1. Erstellen Sie ein bestimmtes Segment, das Treffer aus der betreffenden [!DNL Target] -Aktivität enthält, und dann
1. Filtern Sie die Metrik [!UICONTROL Visits] mit diesem Segment.

**Erstellen des Segments:**

1. Wählen Sie die Option **[!UICONTROL Components > Create Segment]** in der Symbolleiste [!DNL Analysis Workspace] aus.
2. Geben Sie einen **[!UICONTROL Title]** für Ihr Segment an. Im folgenden Beispiel trägt das Segment den Namen [!DNL "Hit with specific Auto-Target activity"].
3. Ziehen Sie die Dimension **[!UICONTROL Target Activities]** in den Abschnitt &quot;Segment **[!UICONTROL Definition]**&quot;.
4. Verwenden Sie den Operator **[!UICONTROL equals]** .
5. Suchen Sie nach Ihrer spezifischen [!DNL Target] -Aktivität.
6. Klicken Sie auf das Zahnradsymbol und wählen Sie dann &quot;**[!UICONTROL Attribution model > Instance]**&quot;, wie in der Abbildung unten dargestellt.
7. Klicken Sie auf **[!UICONTROL Save]**.

![Segment in [!DNL Analysis Workspace]](assets/Figure5.png)

*Abbildung 5: Verwenden Sie ein Segment wie das hier gezeigte, um die Metrik [!UICONTROL Visits] in Ihrem A4T nach [!UICONTROL Auto-Target] Bericht zu filtern*

Nachdem das Segment erstellt wurde, verwenden Sie es zum Filtern der Metrik [!UICONTROL Visits] , sodass die Metrik [!UICONTROL Visits] nur Besuche enthält, bei denen der Benutzer mit der Aktivität [!DNL Target] interagiert hat.

**So filtern Sie [!UICONTROL Visits] mit diesem Segment:**

1. Ziehen Sie das neu erstellte Segment aus der Komponenten-Symbolleiste und bewegen Sie den Mauszeiger über die Basis der Metrikbezeichnung **[!UICONTROL Visits]** , bis eine blaue **[!UICONTROL Filter by]** Meldung angezeigt wird.
2. Lassen Sie das Segment frei. Der Filter wird auf diese Metrik angewendet.

Das endgültige Bedienfeld wird wie folgt angezeigt:

![[!UICONTROL Experiences by Activity Conversions] Bedienfeld in [!DNL Analysis Workspace]](assets/Figure6.png)

*Abbildung 6: Berichtsfenster mit dem Segment &quot;Treffer mit bestimmter Aktivität vom Typ Automatisches Targeting&quot;, das auf die Metrik [!UICONTROL Visits] angewendet wird. Dieses Segment stellt sicher, dass nur Besuche in den Bericht aufgenommen werden, bei denen ein Benutzer tatsächlich mit der betreffenden [!DNL Target] -Aktivität interagiert hat.*

## Stellen Sie sicher, dass die Zielmetrik und Attribution mit Ihrem Optimierungskriterium übereinstimmen.

Durch die A4T-Integration kann das [!UICONTROL Auto-Target] ML-Modell *trainiert* werden, indem dieselben Konversionsereignisdaten verwendet werden, die [!DNL Adobe Analytics] zum Generieren von Leistungsberichten verwendet *.* Es gibt jedoch bestimmte Annahmen, die bei der Interpretation dieser Daten bei der Schulung der ML-Modelle zugrunde gelegt werden müssen, die sich von den Standardannahmen unterscheiden, die während der Berichterstellungsphase in [!DNL Adobe Analytics] vorgenommen wurden.

Insbesondere verwenden die ML-Modelle [!DNL Adobe Target] ein besuchsspezifisches Attributionsmodell. Das heißt, die ML-Modelle gehen davon aus, dass eine Konversion im selben Besuch wie eine Inhaltsanzeige für die Aktivität erfolgen muss, damit die Konversion der vom ML-Modell getroffenen Entscheidung &quot;zugeordnet&quot;wird. Dies ist erforderlich, damit [!DNL Target] eine zeitnahe Schulung seiner Modelle gewährleistet. [!DNL Target] kann nicht bis zu 30 Tage auf eine Konversion warten (das standardmäßige Attributionsfenster für Berichte in [!DNL Adobe Analytics]), bevor es in die Trainings-Daten für seine Modelle aufgenommen wird.

Daher kann der Unterschied zwischen der von den [!DNL Target] -Modellen (während des Trainings) verwendeten Attribution und der bei der Abfrage von Daten verwendeten Standardzuordnung (während der Berichterstellung) zu Diskrepanzen führen. Es kann sogar so aussehen, dass die ML-Modelle nur schlecht funktionieren, wenn das Problem in der Tat mit der Attribution liegt.

>[!TIP]
>
>Wenn die ML-Modelle für eine Metrik optimiert werden, die anders zugeordnet ist als die Metriken, die Sie in einem Bericht anzeigen, funktionieren die Modelle möglicherweise nicht erwartungsgemäß. Um dies zu vermeiden, stellen Sie sicher, dass die Zielmetriken in Ihrem Bericht dieselbe Metrikdefinition und -zuordnung verwenden, die von den [!DNL Target] ML-Modellen verwendet werden.

Die genaue Metrikdefinition und die Attributionseinstellungen hängen vom [Optimierungskriterium](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank} ab, das Sie bei der Erstellung der Aktivität angegeben haben.

### Zieldefinierte Konversionen oder [!DNL Analytics] Metriken mit *Metrikwert pro Besuch maximieren*

Wenn es sich bei der Metrik um eine [!DNL Target] Konversion oder um eine [!DNL Analytics] Metrik mit dem Wert **Metrik pro Besuch maximieren** handelt, ermöglicht die Zielmetrikdefinition, dass im selben Besuch mehrere Konversionsereignisse auftreten.

Gehen Sie wie folgt vor, um Zielmetriken anzuzeigen, die dieselbe Attributionsmethodik aufweisen, die von den [!DNL Target] ML-Modellen verwendet wird:

1. Bewegen Sie den Mauszeiger über das Zahnradsymbol der Zielmetrik:

   ![getriebe.png](assets/gearicon.png)

1. Scrollen Sie aus dem resultierenden Menü zu **[!UICONTROL Data settings]**.
1. Wählen Sie &quot;**[!UICONTROL Use non-default  attribution model]**&quot;(falls noch nicht ausgewählt).

   ![non-defaultattributionmodel.png](assets/non-defaultattributionmodel.png)

1. Klicken Sie auf **[!UICONTROL Edit]**.
1. Wählen Sie **[!UICONTROL Model]**: **[!UICONTROL Participation]** und **[!UICONTROL Lookback window]**: **[!UICONTROL Visit]** aus.

   ![ParticipationbyVisit.png](assets/ParticipationbyVisit.png)

1. Klicken Sie auf **[!UICONTROL Apply]**.

Diese Schritte stellen sicher, dass Ihr Bericht die Zielmetrik der Anzeige des Erlebnisses zuordnet, wenn das Zielmetrikereignis *beliebige Zeit* (&quot;Beitrag&quot;) im selben Besuch stattfand, in dem ein Erlebnis angezeigt wurde.

### [!DNL Analytics] Metriken mit *Konversionsraten bei individuellen Besuchen*

**Definieren des Besuchs mit positivem Metriksegment**

In dem Szenario, in dem Sie *die Konversionsrate individueller Besuche maximieren* als Optimierungskriterium ausgewählt haben, ist die korrekte Definition der Konversionsrate der Anteil der Besuche, in dem der Metrikwert positiv ist. Dies kann erreicht werden, indem ein Segment erstellt wird, das nach Besuchen mit einem positiven Wert der Metrik filtert und dann die Besuchsmetrik filtert.

1. Wählen Sie wie zuvor die Option **[!UICONTROL Components > Create Segment]** in der Symbolleiste [!DNL Analysis Workspace] aus.
2. Geben Sie einen **[!UICONTROL Title]** für Ihr Segment an.

   Im folgenden Beispiel trägt das Segment den Namen [!DNL "Visits with an order"].

3. Ziehen Sie die Basismetrik, die Sie in Ihrem Optimierungsziel verwendet haben, in das Segment.

   Im folgenden Beispiel verwenden wir die Metrik **Bestellungen** , sodass die Konversionsrate den Anteil der Besuche misst, bei denen eine Bestellung aufgezeichnet wird.

4. Wählen Sie oben links im Segmentdefinitionsbehälter **[!UICONTROL Include]** **Besuch** aus.
5. Verwenden Sie den Operator **[!UICONTROL is greater than]** und legen Sie den Wert auf 0 fest.

   Ist der Wert auf 0 gesetzt, bedeutet dies, dass dieses Segment Besuche umfasst, bei denen die Bestellungsmetrik positiv ist.

6. Klicken Sie auf **[!UICONTROL Save]**.

![Abbildung7.png](assets/Figure7.png)

*Abbildung 7: Die Segmentdefinition, die nach Besuchen mit einer positiven Reihenfolge filtert. Abhängig von der Optimierungsmetrik Ihrer Aktivität müssen Sie Bestellungen durch eine entsprechende Metrik ersetzen*

**Wenden Sie dies auf die Besuche in der Aktivitätsgefilterten Metrik an**

Dieses Segment kann jetzt verwendet werden, um nach Besuchen mit einer positiven Anzahl von Bestellungen zu filtern und dort, wo ein Treffer für die [!DNL Auto-Target] -Aktivität stattgefunden hat. Das Verfahren zum Filtern einer Metrik ähnelt dem vorherigen und nach Anwendung des neuen Segments auf die bereits gefilterte Besuchsmetrik sollte das Berichtsbedienfeld wie in Abbildung 8 dargestellt aussehen

![Abbildung8.png](assets/Figure8.png)

*Abbildung 8: Berichtbereich mit der korrekten Konversionsmetrik für Unique Visits: die Anzahl der Besuche, bei denen ein Treffer aus der Aktivität aufgezeichnet wurde und bei denen die Konversionsmetrik (Bestellungen in diesem Beispiel) ungleich null war.*

## Endlicher Schritt: Erstellen Sie eine Konversionsrate, die die oben genannte Magie erfasst

Mit den Änderungen an den Metriken [!UICONTROL Visit] und [!DNL Auto-Target] in den vorherigen Abschnitten sollten Sie die letzte Änderung an Ihrem standardmäßigen A4T-Berichtsbereich für  vornehmen, indem Sie Konversionsraten erstellen, die das richtige Verhältnis - das der korrigierten Zielmetrik - zu einer entsprechend gefilterten Metrik &quot;Besuche&quot;aufweisen.

Erstellen Sie dazu einen [!UICONTROL Calculated Metric] , indem Sie die folgenden Schritte ausführen:

1. Wählen Sie die Option **[!UICONTROL Components > Create Metric]** in der Symbolleiste [!DNL Analysis Workspace] aus.
1. Geben Sie einen **[!UICONTROL Title]** für Ihre Metrik an. Beispiel: &quot;Besuchskorrigierte Konversionsrate für Aktivität XXX&quot;.
1. Wählen Sie **[!UICONTROL Format]** = Prozent und **[!UICONTROL Decimal Places]** = 2.
1. Ziehen Sie die relevante Zielmetrik für Ihre Aktivität (z. B. [!UICONTROL Activity Conversions]) in die Definition und verwenden Sie das Zahnradsymbol für diese Zielmetrik, um das Attributionsmodell auf (Beitrag|Besuch) anzupassen, wie zuvor beschrieben.
1. Wählen Sie oben rechts im Abschnitt **[!UICONTROL Definition]** den Wert **[!UICONTROL Add > Container]** aus.
1. Wählen Sie zwischen den beiden Behältern den Operator Division () aus.
1. Ziehen Sie Ihr zuvor erstelltes Segment namens &quot;Treffer mit bestimmter [!UICONTROL Auto-Target] -Aktivität&quot;in dieses Tutorial für diese spezifische [!DNL Auto-Target] -Aktivität.
1. Ziehen Sie die Metrik **[!UICONTROL Visits]** in den Segmentbehälter.
1. Klicken Sie auf **[!UICONTROL Save]**.

>[!TIP]
>
> Sie können diese Metrik auch mit der Funktion [für schnell berechnete Metriken](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html) erstellen.

Die vollständige Definition der berechneten Metrik wird hier angezeigt.

![Abbildung9.png](assets/Figure9.png)

*Abbildung 7: Die Metrikdefinition für die besuchskorrigierte und zuordnungskorrigierte Modellkonversionsrate. (Beachten Sie, dass diese Metrik von Ihrer Zielmetrik und -aktivität abhängt. Mit anderen Worten: Diese Metrikdefinition kann nicht über mehrere Aktivitäten hinweg wiederverwendet werden.)*

>[!IMPORTANT]
>
>Die Metrik [!UICONTROL Conversion] der Rate aus dem A4T-Bedienfeld ist nicht mit dem Konversionsereignis oder der Normalisierungsmetrik in der Tabelle verknüpft. Wenn Sie die in diesem Tutorial vorgeschlagenen Änderungen vornehmen, passt sich die [!UICONTROL Conversion]-Rate nicht automatisch an die Änderungen an. Wenn Sie daher die Änderung an der Konversionsereigniszuordnung oder der Normalisierungsmetrik (oder beidem) vornehmen, müssen Sie sich als letzten Schritt merken, um auch die [!UICONTROL Conversion] -Rate zu ändern, wie oben gezeigt.

## Zusammenfassung: Endgültiges Beispiel für [!DNL Analysis Workspace] für [!UICONTROL Auto-Target] Berichte

Wenn Sie alle oben genannten Schritte in einem Bedienfeld zusammenfassen, zeigt die Abbildung unten eine vollständige Ansicht des empfohlenen Berichts für [!UICONTROL Auto-Target] A4T-Aktivitäten. Dieser Bericht entspricht dem Bericht, den die [!DNL Target] ML-Modelle zur Optimierung Ihrer Zielmetrik verwenden. Der Bericht enthält alle in diesem Tutorial behandelten Nuancen und Empfehlungen. Dieser Bericht ähnelt auch den Zählmethodiken, die bei herkömmlichen [!DNL Target] berichtgesteuerten [!UICONTROL Auto-Target] Aktivitäten verwendet werden.

Klicken Sie auf , um das Bild zu erweitern.

![Abgeschlossener A4T-Bericht im [!DNL Analysis Workspace]](assets/Figure10.png "A4T-Bericht in Analysis Workspace"){width="600" zoomable="yes"}

*Abbildung 10: Der endgültige A4T [!UICONTROL Auto-Target] -Bericht in [!DNL Adobe Analytics] [!DNL Workspace], der alle Anpassungen an Metrikdefinitionen kombiniert, die in den vorherigen Abschnitten dieses Tutorials beschrieben wurden.*
