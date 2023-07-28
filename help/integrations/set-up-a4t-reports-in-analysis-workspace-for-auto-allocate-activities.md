---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!UICONTROL Automatische Zuordnung] Tätigkeiten
description: Konfigurieren von A4T-Berichten in [!DNL Analysis Workspace] zum Abrufen der erwarteten Ergebnisse während der Ausführung [!UICONTROL Automatische Zuordnung] Aktivitäten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: dddb90e66d127782d4fe1347bd43553cd8c04d58
workflow-type: tm+mt
source-wordcount: '1303'
ht-degree: 0%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Allocate] activities

Ein [!DNL Auto-Allocate] -Aktivität einen Gewinner unter zwei oder mehr Erlebnissen identifiziert und Ihren Traffic automatisch an den Gewinner weiterleitet, während der Test weiter ausgeführt und das Lernen fortgesetzt wird. Die [!UICONTROL Analytics for Target] (A4T)-Integration für [!UICONTROL Automatische Zuordnung] ermöglicht Ihnen, Ihre Berichtsdaten in [!DNL Adobe Analytics]und Sie können sogar für benutzerdefinierte Ereignisse oder Metriken optimieren, die in [!DNL Analytics].

Obwohl Rich-Analytics-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace], einige Änderungen an der Standardeinstellung **[!UICONTROL Analytics for Target]** -Bedienfeld möglicherweise für die korrekte Interpretation erforderlich [!DNL Auto-Allocate] Aktivitäten aufgrund der Nuancen in [Optimierungsmetrikkriterien](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank}.

Dieses Tutorial führt Sie durch die empfohlenen Änderungen zur Analyse [!DNL Auto-Allocate] Aktivitäten in [!DNL Analysis Workspace]. Die Schlüsselkonzepte sind:

* [!UICONTROL Besucher] sollte immer als Normalisierungsmetrik in [!DNL Auto-Allocate] Aktivitäten.
* Wenn die Metrik eine [!DNL Adobe Analytics] Metrik, variiert die Berechnung der Konversionsrate je nach dem Typ der Optimierungskriterien, die während der Aktivitätseinrichtung definiert wurden.
   * Der &quot;Metrikwert pro Besucher maximieren&quot;: Konversionsratenzähler ist der reguläre Metrikwert in [!DNL Adobe Analytics] (Dies wird standardmäßig im [!UICONTROL Analytics for Target] Bedienfeld in A[!DNL nalysis Workspace]).
      * Das bedeutet: Maximiert die Anzahl der Konversionen pro Besucher (&quot;Zählung pro Besucher&quot;).
      * Für diese Methode ist kein zusätzliches Segment erforderlich, um die im [!DNL Target] Benutzeroberfläche.
   * Die &quot;Unique Visitor-Konversionsrate maximieren&quot;: Konversionsratenzähler ist die Anzahl der Unique Visitors mit einem positiven Wert der Metrik.
      * Das bedeutet: Maximiert die Anzahl der Besucher, die konvertieren (&quot;einmal pro Besucher zählen&quot;).
      * Diese Methode *TUN* die Erstellung eines zusätzlichen Segments in der Berichterstellung erforderlich, um die in der Variablen [!DNL Target] Benutzeroberfläche.

* Wenn Ihre Optimierungsmetrik eine [!DNL Target] definierte Konversionsmetrik, die standardmäßige **[!UICONTROL Analytics for Target]** Bedienfeld in [!DNL Analysis Workspace] verarbeitet die Konfiguration Ihres Bedienfelds.
* Für alle [!UICONTROL Automatische Zuordnung] vor der [!DNL Target Standard/Premium] Version 23.3.1 (30. März 2023) [!DNL Analytics Workspace] und [!DNL Target] denselben Wert anzeigen für [!UICONTROL Vertrauen].

  Für alle [!UICONTROL Automatische Zuordnung] Aktivitäten, die nach dem 30. März 2023 erstellt wurden, die Konfidenzintervallwerte, die in [!DNL Analysis Workspace] nicht die [konservativere Statistiken, die von [!UICONTROL Automatische Zuordnung]](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html#section_98388996F0584E15BF3A99C57EEB7629){target=_blank} in , wenn diese Aktivitäten *both* der folgenden Bedingungen:

   * [!DNL Analytics] als Berichtsquelle (A4T)
   * [!DNL Analytics] Optimierungsmetriken

  Die Konfidenzmetriken sollten aus dem A4T-Bedienfeld entfernt werden. Verweisen Sie stattdessen auf diese Werte in [!DNL Target] Berichterstellung.

## Erstellen Sie A4T für [!DNL Auto-Allocate] Bedienfeld in [!DNL Analysis Workspace]

So erstellen Sie ein A4T-Bedienfeld für eine [!DNL Auto-Allocate] Bericht beginnt mit der **[!UICONTROL Analytics for Target]** Bedienfeld in [!DNL Analysis Workspace], wie unten dargestellt. Wählen Sie dann die folgenden Optionen aus:

1. **[!UICONTROL Kontrollerlebnis]**: Sie können ein beliebiges Erlebnis auswählen.
1. **[!UICONTROL Normalisierungsmetrik]**: Wählen Sie Besucher aus (Besucher sind standardmäßig im A4T-Bedienfeld enthalten). [!DNL Auto-Allocate] Normalisiert Konversionsraten immer nach Unique Visitors.
1. **[!UICONTROL Erfolgsmetriken]**: Wählen Sie dieselbe Metrik aus, die Sie bei der Erstellung der Aktivität verwendet haben. Wenn dies eine [!DNL Target] definierte Konversionsmetrik auswählen **Aktivitätskonvertierung**. Andernfalls wählen Sie die [!DNL Adobe Analytics] -Metrik verwenden.

![[!UICONTROL Analytics for Target] Bedienfeldeinstellungen für [!DNL Auto-Allocate] Aktivitäten.](assets/AAFigure1.png)

*Abbildung 1: [!UICONTROL Analytics for Target] Bedienfeldeinstellungen für [!DNL Auto-Allocate] Aktivitäten.*

Sie können auch zu einem vordefinierten **[!UICONTROL Analytics for Target]** angezeigt, wenn Sie auf den Link im Berichtsbildschirm in [!DNL Adobe Target].

## [!DNL Target] [!UICONTROL Konversion] Metriken [!DNL Analytics] Metriken mit Optimierungskriterien &quot;Metrikwert pro Besucher maximieren&quot;

Wenn die Zielmetrik entweder:

* Eine Target-Konversionsmetrik
* Analytics-Metrik mit dem Optimierungskriterium &quot;Metrikwert pro Besucher maximieren&quot;

Im standardmäßigen A4T-Bedienfeld wird der Bericht automatisch konfiguriert.

Ein Beispiel für dieses Bedienfeld wird für die [!UICONTROL Umsatz] Metrik, wobei &quot;Metrikwert pro Besucher maximieren&quot;zum Zeitpunkt der Aktivitätserstellung als Optimierungskriterium ausgewählt wurde. Wie bereits erwähnt, [!DNL Auto-Allocate] verwendet konservativere Konfidenzberechnungen im Vergleich zu den in **[!UICONTROL Analytics for Target]** Bedienfeld. Adobe empfiehlt, die Konfidenzmetrik aus dem A4T-Bedienfeld sowie die zugehörigen Metriken für die untere und obere Steigerung zu entfernen. Referenzieren Sie stattdessen die Konfidenzwerte in [!DNL Target] Berichterstellung.

>[!NOTE]
>
>Konfidenzwerte in A4T-Berichten sind weniger konservativ als [!DNL Target] Berichte erstellen und möglicherweise vorzeitig einen Gewinner für eine [!UICONTROL Automatische Zuordnung] -Aktivität.


![[!UICONTROL Analytics for Target - Bericht zur automatischen Zuordnung] panel](assets/AAFigure2.png)

*Abbildung 2: Der empfohlene Bericht für [!DNL Auto-Allocate] Aktivitäten mit [!DNL Analytics] Metrik Optimieren des Metrikwerts pro Besucher. Für diese Metriktypen sowie [!DNL Target] definierte Konversionsmetriken, die standardmäßige **[!UICONTROL Analytics for Target]**Bedienfeld in [!DNL Analysis Workspace] verwendet werden.*

## [!DNL Analytics] Metriken mit Optimierungskriterien zur &quot;Maximierung der Unique Visitor-Konversionsrate&quot;

Das Optimierungskriterium &quot;Konversionsrate Unique Visitors maximieren&quot;bezieht sich auf die Anzahl der Besucher, für die der Metrikwert positiv ist. Wenn die Konversionsrate beispielsweise als Umsatz definiert ist, optimiert das Kriterium &quot;Individuelle Besucherkonversionsrate maximieren&quot;die Anzahl der Unique Visitors, deren Umsatz größer als 0 war. Mit anderen Worten würde dieses Kriterium die Anzahl der Besucher maximieren, die Umsatz generieren, und nicht den Wert des Umsatzes selbst.

>[!NOTE]
>
>Die hier referenzierte Konversionsrate kann sich auf Aktionen außerhalb von Bestellungen beziehen, z. B. Klicks, Impressionen usw. In diesen Fällen bestünde das Kriterium weiterhin darin, die Anzahl der Besucher zu maximieren, die auf die Seite klicken bzw. diese anzeigen.

Die [!DNL Analytics for Target] Bedienfeld in [!DNL Analysis Workspace] muss geändert werden, wenn dieses Optimierungskriterium mit einer [!DNL Adobe Analytics] Metrik.

Wenn dieses Optimierungskriterium verwendet wird, ist die Erfolgsmetrik die Anzahl der Unique Visitors, für die die Konversionsmetrik positiv war. Um diesen Wert anzuzeigen, muss daher ein neues Segment erstellt werden, das auf Treffer mit einem positiven Wert für die Metrik filtert.

Erstellen Sie dieses Segment wie folgt:

1. Wählen Sie die **[!UICONTROL Komponenten]** > **[!UICONTROL Segment erstellen]** in der [!DNL Analysis Workspace] Symbolleiste.
1. Ziehen Sie die zur Zeit der Aktivitätserstellung verwendete Metrik aus dem linken Bereich in den **[!UICONTROL Definition]** -Feld des Segments.
1. Wählen Sie die Werte der Metrik aus, die **größer als** ein numerischer Wert von 0.
1. Aus dem **[!UICONTROL Einschließen]** Dropdown-Liste auswählen **[!UICONTROL Besucher]**.
1. Geben Sie Ihrem Segment einen geeigneten Namen.

Ein Beispiel für die Segmenterstellung finden Sie in der folgenden Abbildung, wobei die Erfolgsmetrik [!UICONTROL Besucher mit positivem Umsatz].

![[!UICONTROL Besucher mit positivem Umsatz] Segment in [!DNL Analysis Workspace]](assets/AAFigure3.png)

*Abbildung 3: Segmenterstellung für [!DNL Adobe Analytics] Metriken mit Optimierungskriterien gleich &quot;[!UICONTROL Maximieren der Unique Visitor-Konversionsrate].&quot; In diesem Beispiel lautet die Metrik [!UICONTROL Umsatz]und das Optimierungsziel darin besteht, die Anzahl der Besucher mit positivem Umsatz zu maximieren.*

Nachdem das entsprechende Segment erstellt wurde, können Sie die Standardeinstellung ändern  **[!UICONTROL Analytics for Target]** Bedienfeld in [!DNL Analysis Workspace] um die Werte des Optimierungskriteriums anzuzeigen. Gehen Sie dazu wie folgt vor:

1. Sekunde hinzufügen **Unique Visitors** Metrik neben dem vorhandenen [!UICONTROL Besucher] Metrikspalte.
2. Ziehen Sie das neu erstellte Segment unter die erste Spalte, um ein Bedienfeld zu erstellen, das Abbildung 4 ähnelt. Beachten Sie den Unterschied in den Werten der Spalten: Die Anzahl der Unique Visitors mit positivem Umsatz sollte einen Bruchteil der Gesamtzahl der Unique Visitors darstellen, die jedem Erlebnis zugeordnet sind (wie unten dargestellt).

   ![Abbildung4.png](assets/AAFigure4.png)

   *Abbildung 4: Filter [!UICONTROL Unique Visitors] durch das neu erstellte Segment*

3. Eine Konversionsrate kann [schnell berechnet](https://experienceleague.adobe.com/docs/analytics-learn/tutorials/components/calculated-metrics/quick-calculated-metrics-in-analysis-workspace.html) durch Hervorhebung der ersten und zweiten Spalte, Rechtsklick, Auswahl **[!UICONTROL Metrik aus Auswahl erstellen]** > **[!UICONTROL Dividieren]**.

   Die standardmäßige Konversionsrate sollte entfernt und durch diese neue berechnete Metrik ersetzt werden, wie in der Abbildung unten dargestellt. Möglicherweise müssen Sie die neu erstellte berechnete Metrik bearbeiten, um sie als **[!UICONTROL Format]** > **[!UICONTROL Prozent]** bis zu zwei Dezimalstellen, wie dargestellt.

   ![Abbildung 5.png](assets/AAFigure5.png)

   *Abbildung 5: Das endgültige [!UICONTROL Automatische Zuordnung] Bedienfeld, das die Konversionsraten für eine binarisierte Metrik zur Umsatzkonvertierung anzeigt*

## Zusammenfassung

Die Schritte in diesem Tutorial zeigten, wie Sie das [!DNL Analysis Workspace] zur Anzeige [!UICONTROL Automatische Zuordnung] Berichtsdaten.

Zusammenfassung:

* Wenn die Metrik eine [!DNL Target] definierte Konversionsmetrik oder [!DNL Adobe Analytics] Metrik mit dem Optimierungskriterium &quot;Metrikwert pro Besucher maximieren&quot;verwendet werden, sollte das standardmäßige Workspace-Bedienfeld verwendet werden, das mit Besuchern als Normalisierungsmetrik konfiguriert wurde.
* Wenn die Metrik eine [!DNL Adobe Analytics] Metrik mit dem Optimierungskriterium &quot;Unique Visitor-Konversionsrate maximieren&quot;müssen Sie den Anteil der Besucher mit positivem Metrikwert im Vergleich zu den Gesamtbesuchern bestimmen. Dies geschieht durch Erstellen eines entsprechenden Segments, das die [!UICONTROL Unique Visitor] auf dieser Metrik.
