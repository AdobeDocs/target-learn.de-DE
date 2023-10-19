---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!UICONTROL Automatische Zuordnung] Tätigkeiten
description: Konfiguration [!UICONTROL Analytics for Target] (A4T)-Berichte in [!DNL Adobe] [!DNL Analysis Workspace] beim Ausführen [!UICONTROL Automatische Zuordnung] Aktivitäten.
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: b22d51d7d231d67af179622755fb4f7ef83474a8
workflow-type: tm+mt
source-wordcount: '1590'
ht-degree: 0%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Allocate] activities

Ein [!UICONTROL Automatische Zuordnung] Aktivität in [!DNL Adobe Target] identifiziert einen Gewinner unter zwei oder mehr Erlebnissen und ordnet den Besucher-Traffic automatisch dem Gewinner zu, während der Test weiter ausgeführt und das Lernen fortgesetzt wird. Die [!UICONTROL Analytics for Target] (A4T)-Integration für [!UICONTROL Automatische Zuordnung] ermöglicht die Anzeige von Berichtsdaten in [!DNL Adobe Analytics]und Sie können für benutzerdefinierte Ereignisse oder Metriken optimieren, die in [!DNL Analytics].

Obwohl Rich-Analytics-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace], einige Änderungen an der Standardeinstellung [!UICONTROL Analytics for Target] -Bedienfeld möglicherweise für die korrekte Interpretation erforderlich [!UICONTROL Automatische Zuordnung] Aktivitäten. Diese Änderungen sind aufgrund der Nuancen in [Optimierungsmetrikkriterien](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank}.

Für jeden Optimierungstyp ist eine andere Berichtskonfiguration in A4T erforderlich, wie im folgenden Beispiel:

* Verwenden eines [!DNL Analytics] Metrik

   * [!UICONTROL Metrikwert pro Besucher maximieren]
   * [!UICONTROL Maximieren der Unique Visitor-Konversionsrate]

* Verwenden eines [!DNL Target]-definierte Konversionsmetrik

In diesem Tutorial werden die allgemeinen A4T-Anleitungen und Kriterienspezifische Schritte zur Berichtskonfiguration behandelt.

## Analytics-Metriken mit &quot;[!UICONTROL Metrikwert pro Besucher maximieren]&quot;Optimierungskriterien

**Definition**: (Gesamtwert der Metrik) / ( Anzahl der Besucher)

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | [!DNL Target]-ausgelöster Bericht | A4T-Bereichsbericht |
| --- | --- | --- |
| Maximieren Sie den Metrikwert für eine [!DNL Analytics] Metrik | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>[!UICONTROL Steigerung (niedrig)] und [!UICONTROL Steigerung (hoch)] sollte entfernt werden.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li><li>Die Konversionsratenmetrik sollte in &quot;Metrik/Besucher&quot;umbenannt werden.</li></ul> | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>[!UICONTROL Steigerung (niedrig)] und [!UICONTROL Steigerung (hoch)] sollte entfernt werden.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li><li>Die Konversionsratenmetrik sollte in &quot;Metrik/Besucher&quot;umbenannt werden.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten übereinstimmen, die in der Variablen [!DNL Target] Bericht. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li></ul> |

![Metrikwert für Umsatz maximieren](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] Metriken mit[!UICONTROL Unique Visitor-Konversionsrate]&quot;Optimierungskriterien

**Definition**: ( Anzahl der Unique Visitors mit einem positiven Wert der Metrik) / (Gesamtanzahl der Unique Visitors)

Beispiel: Angenommen, Ihre Optimierungsmetrik lautet [!UICONTROL Umsatz]. Die Aktivität umfasst fünf Unique Visitors und drei dieser Unique Visitors tätigen einen Kauf. In diesem Beispiel ist dieser Wert = (3 Besucher, für die [!UICONTROL Umsatz] ist positiv) / (5 Unique Visitors insgesamt) = 0,6 = 60 %.

>[!NOTE]
>
>Die hier referenzierte Konversionsrate kann sich auf Aktionen außerhalb von Bestellungen beziehen, z. B. Klicks, Impressionen usw. In diesen Fällen bestünde das Kriterium weiterhin darin, die Anzahl der Besucher zu maximieren, die auf die Seite klicken bzw. diese anzeigen.

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Von Target ausgelöster Bericht | A4T-Bereichsbericht |
| --- | --- | --- |
| Maximieren Sie Konversionen für eine [!DNL Analytics] Metrik | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>Alle [!UICONTROL Steigerung] -Metriken entfernt werden.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. (Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li></ul> | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>Alle [!UICONTROL Steigerung] -Metriken entfernt werden.</li><li>Erstellen Sie ein Segment, um Besucher mit einem positiven Metrikwert zu filtern, der die analysierte Aktivität angesehen hat. Weitere Informationen finden Sie unter [Segment erstellen](#segment) unten.</li><li>Ersetzen Sie die automatisch ausgefüllten [!UICONTROL Konversionsrate] Metrik, sodass dies die Division zwischen [!UICONTROL Unique Visitors] mit einem positiven Metrikwert und Unique Visitors. Weitere Informationen finden Sie unter [Konversionsratenmetrik aktualisieren](#update-conversion-metric) unten.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten übereinstimmen, die in der Variablen [!DNL Target] Bericht. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li></ul> |

### Standardbericht des A4T-Bedienfelds - Zusätzliche Anleitungen

Die folgenden Abschnitte enthalten weitere Informationen über zusätzliche Anleitungen bei der Einrichtung Ihres standardmäßigen A4T-Bedienfeldberichts.

#### Segment erstellen {#segment}

1. Klicken Sie auf **&quot;+&quot;-Zeichen** neben **[!UICONTROL Segmente]** in der linken Leiste.

   ![Pluszeichen neben Segmenten in der linken Leiste.](/help/integrations/assets/plus-sign.png)

1. Geben Sie dem Segment &quot;Besucher mit positivem Metrikwert&quot;einen Titel.
1. under **[!UICONTROL Definition]**, neben **[!UICONTROL Einschließen]** auswählen **[!UICONTROL Besucher]**.
1. under **[!UICONTROL Definition]** wählen Sie die Optimierungsmetrik in Ihrer Aktivität aus.

   In diesem Beispiel nehmen Sie an, [!UICONTROL Umsatz] als Optimierungsmetrik.

1. Wählen Sie &quot;[!UICONTROL größer als]&quot;, und geben Sie dann &quot;0&quot;an.

   Diese Einstellungen werden für alle Besucher mit einem positiven Metrikwert gefiltert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Positiver Metrikwert](/help/integrations/assets/positive-metric-value.png)

1. Fügen Sie das neu erstellte Segment namens &quot;Besucher mit positivem Metrikwert&quot;zum A4T-Bedienfeld hinzu.
1. Ziehen Sie die [!UICONTROL Unique Visitors] in derselben Spalte wie die Metrik &quot;Besucher mit positivem Metrikwert&quot;angezeigt.

   Diese Konfiguration erstellt ein Segment aller Unique Visitors, für die der Metrikwert positiv ist. In diesem Beispiel alle Unique Visitors, deren Umsatz größer als null war.

#### Aktualisieren Sie die [!UICONTROL Konversionsrate] Metrik {#update-conversion-metric}

1. Wenn Sie dies noch nicht getan haben, entfernen Sie die vorhandene [!UICONTROL Konversionsrate] -Spalte im Bedienfeld aus, wie unten beschrieben.
1. Fügen Sie eine Metrik hinzu, indem Sie auf das Pluszeichen (+) neben dem **[!UICONTROL Metriken]** in der linken Leiste.
1. Benennen Sie die Metrik &quot;Konversionsrate&quot;und definieren Sie sie als &quot;([!UICONTROL Unique Visitors] mit positivem Metrikwert)&quot;durch &quot;Unique Visitors&quot;geteilt, wie unten dargestellt.

   Fügen Sie das neu erstellte Segment (die unten definierten Schritte) von &quot;Besucher mit positivem Metrikwert&quot;, den Division-Operator, die Metrik &quot;Unique Visitors&quot;im Zähler und &quot;Unique Visitors&quot;als Nenner hinzu.

   ![Konversionsrate im A4T-Bedienfeld.](/help/integrations/assets/conversion-rate.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Ziehen Sie die neu erstellte Metrik &quot;Konversionsrate&quot;per Drag-and-Drop in Ihr vorhandenes Bedienfeld.
1. Klicken Sie auf das Zahnradsymbol und deaktivieren Sie dann die **[!UICONTROL Prozent]** -Kontrollkästchen, da dieser Wert zu Verwirrung führen kann.

   Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

   ![Konversionsrate eindeutiger Besuche im A4T-Bereichsbericht](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target]-definierte Konversionsrate

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Von Target ausgelöster Bericht | A4T-Bereichsbericht |
| --- | --- | --- |
| [!DNL Analytics] Reporting mit [!DNL Target] Konversionsmetrik | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>[!UICONTROL Steigerung (niedrig)] und [!UICONTROL Steigerung (hoch)] sollte entfernt werden.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li></ul> | <ul><li>[!UICONTROL Vertrauen] -Metriken entfernt werden.</li><li>[!UICONTROL Steigerung (niedrig)] und [!UICONTROL Steigerung (hoch)] sollte entfernt werden.</li><li>Deaktivieren Sie die Prozentdarstellung aus der [!UICONTROL Konversionsrate] -Spalte, um Verwirrung zu vermeiden. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten übereinstimmen, die in der Variablen [!DNL Target] Bericht. Weitere Informationen finden Sie unter [Allgemeine Leitlinien](#guidance) unten.</li></ul> |

Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

![Aktivitätskonversionen](/help/integrations/assets/optimized-table.png)

## Allgemeine Leitlinien für [!UICONTROL Analytics for Target] (A4T) {#guidance}

Sie können zu einer vordefinierten [!UICONTROL Analytics for Target] durch Klicken auf den Link im Berichtsbildschirm in [!UICONTROL Adobe Target] (Dies wird weiter unten in diesem Handbuch als[!DNL Target]-ausgelöster Bericht&quot;). Alternativ können Sie das A4T-Bedienfeld in [!DNL Analytics] (Details finden Sie weiter unten in diesem Abschnitt).

In den folgenden Abschnitten wird festgelegt, welche Konfigurationen erforderlich sind, je nachdem, welche dieser Methoden Sie auswählen. Die folgenden Schritte dienen jedoch als allgemeine Orientierung:

* Die Konfidenzmetriken sollten unabhängig von der Methode zur Bereichserstellung aus dem A4T-Bedienfeld entfernt werden (beide sind unten beschrieben). Verweisen Sie stattdessen auf diese Werte in [!DNL Target] Berichterstellung. Darüber hinaus können Aktivitätsinhaber in [!DNL Target] Berichterstellung. Details zur Identifizierung des Aktivitätsgewinners finden Sie im Abschnitt [Identifizieren des Aktivitätsinhabers](#winner) unten.
>>
* Um Verwirrung zu vermeiden, deaktivieren Sie die Option &quot;[!UICONTROL Prozent]&quot; Erläuterung der [!UICONTROL Konversionsrate] Metrik. Weitere Informationen finden Sie unter [Ausblenden des Prozentsatzes aus der [!UICONTROL Konversionsrate] column](#hide-percentage) unten.
>>
* Wenn Sie ein A4T-Bedienfeld erstellen, stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit denen Ihrer [!DNL Target] Bericht. Weitere Informationen finden Sie unter [Datum und Uhrzeit im A4T-Bedienfeld ausrichten](#aligning-date-and-time) unten.

### Ausblenden des Prozentsatzes aus der [!UICONTROL Konversionsrate] column {#hide-percentage}

1. Klicken Sie auf **Zahnrad** Symbol neben dem Titel des [!UICONTROL Konversionsrate] Spalte.

   ![Zahnradsymbol in der Spalte Konversionsrate](/help/integrations/assets/coversion-rate-gear-icon.png)

   Die [!UICONTROL Spalte] Das Dialogfeld &quot;Einstellungen&quot;wird angezeigt:

   ![Dialogfeld &quot;Spalteneinstellungen&quot;](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Deaktivieren Sie die **[!UICONTROL Prozent]** aktivieren.

   Ihr A4T-Bedienfeld enthält jetzt keine Prozentsätze als Konversionsrate und Treffer [!DNL Target], wie unten dargestellt:

   ![Spalte &quot;Konversionsrate&quot;ohne Prozentwerte](/help/integrations/assets/no-percentages.png)

### Datum und Uhrzeit im A4T-Bedienfeld ausrichten {#aligning-date-and-time}

1. Überprüfen Sie unter jedem Bedienfeld den Datumsbereich, auf den das Bedienfeld verweist, um sicherzustellen, dass der Datumsbereich mit dem der [!DNL Target] Bericht.

   ![Datumsbereich im A4T-Bedienfeld](/help/integrations/assets/date-range.png)

1. In [!DNL Analytics], setzen Sie den Zeitraum auf 12:00 - 23:59 Uhr.

### Identifizieren des Aktivitätsgewinners {#winner}

[!DNL Auto-Allocate] Die Aktivitätsinhaber werden ausgewählt, wenn eine Gewinnerkonversionsrate mit Konfidenzwerten größer oder gleich 95 % vorliegt. Auf diese Werte sollte im Abschnitt [!DNL Target] Berichte, da Konfidenzberechnungen die konservativeren Methoden widerspiegeln [!DNL Target] empfiehlt [!UICONTROL Automatische Zuordnung] Aktivitäten. Weitere Informationen finden Sie unter [Statistische Garantien für die automatische Zuordnung](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C){target=_blank} im *[!UICONTROL Handbuch für Adobe Target Business Practices]*.

>[!NOTE]
>
Die Abzeichen &quot;Noch kein Gewinner&quot;und &quot;Gewinner&quot;sind im A4T-Bedienfeld unter [!DNL Analysis Workspace]. Außerdem wurde das Siegerabzeichen &quot;Stern&quot;in [!DNL Target] Berichte für [!UICONTROL Automatische Zuordnung] -Aktivitäten ignoriert werden. Weitere Informationen finden Sie unter [Automatische Zuordnung](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa){target=_blank} in *A4T-Unterstützung für Aktivitäten mit automatischer Zuordnung und automatischem Targeting* im *[!UICONTROL Handbuch für Adobe Target Business Practices]*.

### Erstellen Sie A4T für [!UICONTROL Automatische Zuordnung] Bedienfeld in [!DNL Analysis Workspace]

1. So erstellen Sie ein A4T-Bedienfeld für eine [!UICONTROL Automatische Zuordnung] Aktivitätsbericht, beginnen Sie mit der [!UICONTROL Analytics for Target] Bedienfeld in [!DNL Analysis Workspace], wie unten dargestellt.

   ![Analytics for Target - Bericht zur automatischen Zuordnung](/help/integrations/assets/a4t-auto-allocate-report.png)

1. Führen Sie die folgenden Auswahlen aus:

   * **[!UICONTROL Kontrollerlebnis]**: Wählen Sie ein beliebiges Erlebnis aus.
   * **[!UICONTROL Normalisierungsmetrik]**: Auswählen **[!UICONTROL Besucher]** (standardmäßig im A4T-Bedienfeld enthalten). [!UICONTROL Automatische Zuordnung] Normalisiert Konversionsraten immer nach Unique Visitors.
   * **Erfolgsmetriken**: Wählen Sie dieselbe Metrik (Optimierung) aus, die Sie bei der Erstellung der Aktivität verwendet haben. Wenn dies eine [!DNL Target]-definierte Konversionsmetrik auswählen **[!UICONTROL Aktivitätskonvertierung]**. Andernfalls wählen Sie die [!DNL Adobe Analytics] -Metrik verwenden.









