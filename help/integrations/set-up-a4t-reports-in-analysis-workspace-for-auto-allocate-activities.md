---
title: Einrichten von A4T-Berichten in  [!DNL Analysis Workspace] für [!UICONTROL Auto-Allocate] -Aktivitäten
description: Wie konfiguriere ich [!UICONTROL Analytics for Target] (A4T)-Berichte in  [!DNL Adobe] [!DNL Analysis Workspace], wenn ich [!UICONTROL Auto-Allocate] -Aktivitäten ausführe?
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
source-git-commit: 190a67832f378e15090115420bfaf8a4af4b9cb9
workflow-type: tm+mt
source-wordcount: '1341'
ht-degree: 0%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Allocate] -Aktivitäten

Eine [[!UICONTROL Auto-Allocate] -Aktivität](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html){target=_blank} in [!DNL Adobe Target] identifiziert einen Gewinner unter zwei oder mehr Erlebnissen und ordnet den Besucher-Traffic automatisch dem Gewinner zu, während der Test weiter ausgeführt und das Lernen fortgesetzt wird. Mit der Integration von [!UICONTROL Analytics for Target] (A4T) für [!UICONTROL Auto-Allocate] können Sie Berichtsdaten in [!DNL Adobe Analytics] anzeigen und für benutzerdefinierte Ereignisse oder Metriken optimieren, die in [!DNL Analytics] definiert sind.

Obwohl Rich-Analyse-Funktionen in [!DNL Adobe Analytics] [!DNL Analysis Workspace] verfügbar sind, sind möglicherweise einige Änderungen am standardmäßigen Bedienfeld [!UICONTROL Analytics for Target] erforderlich, um [!UICONTROL Auto-Allocate] -Aktivitäten korrekt zu interpretieren. Diese Änderungen sind aufgrund der Nuancen in den [Optimierungsmetrikkriterien](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank} erforderlich.

Für jeden Optimierungstyp ist eine andere Berichtskonfiguration in A4T erforderlich, wie im folgenden Beispiel:

* Verwenden einer [!DNL Analytics] -Metrik

   * [!UICONTROL Maximize metric value per visitor]
   * [!UICONTROL Maximize unique visitor conversion rate]

* Verwenden einer [!DNL Target] definierten Konversionsmetrik

In diesem Tutorial werden die allgemeinen A4T-Anleitungen und Kriterienspezifische Schritte zur Berichtskonfiguration behandelt.

## Analytics-Metriken mit &quot;[!UICONTROL Maximize Metric Value Per Visitor]&quot;-Optimierungskriterien

**Definition**: (Gesamtmetrikwert) / ( Anzahl der Besucher)

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | [!DNL Target]-Bericht ausgelöst | A4T-Bereichsbericht |
| --- | --- | --- |
| Maximieren Sie den Metrikwert für eine [!DNL Analytics] -Metrik. | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Behalten Sie [!UICONTROL Lift (Med)] bei.</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie die Metrik [!UICONTROL Conversion] Rate in &quot;Metrik/Besucher&quot;um.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] Behalten Sie [!UICONTROL Lift (Med)].</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie die Metrik [!UICONTROL Conversion] Rate in &quot;Metrik/Besucher&quot;um.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten im Bericht [!DNL Target] übereinstimmen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

![Metrikwert für Umsatz maximieren](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] Metriken mit den Optimierungskriterien &quot;[!UICONTROL Unique Visitor Conversion Rate]&quot;

**Definition**: ( Anzahl der Unique Visitors mit einem positiven Wert der Metrik) / (Gesamtanzahl der Unique Visitors)

Beispiel: Angenommen, Ihre Optimierungsmetrik ist [!UICONTROL Revenue]. Die Aktivität umfasst fünf Unique Visitors und drei dieser Unique Visitors tätigen einen Kauf. In diesem Beispiel ist dieser Wert = (3 Besucher, für die [!UICONTROL Revenue] positiv ist) / (5 Unique Visitors insgesamt) = 0,6 = 60 %.

>[!NOTE]
>
>Die hier referenzierte Konversionsrate kann sich auf Aktionen außerhalb von Bestellungen beziehen, z. B. Klicks, Impressionen usw. In diesen Fällen bestünde das Kriterium weiterhin darin, die Anzahl der Besucher zu maximieren, die auf die Seite klicken bzw. diese anzeigen.

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Von Target ausgelöster Bericht | A4T-Bereichsbericht |
| --- | --- | --- |
| Maximieren der Konversionen für eine [!DNL Analytics] -Metrik | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie alle drei [!UICONTROL Lift] -Metriken.</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie alle drei [!UICONTROL Lift] -Metriken.</li><li>Erstellen Sie ein Segment, um Besucher mit einem positiven Metrikwert zu filtern, der die analysierte Aktivität angezeigt hat. Siehe [Erstellen eines Segments](#segment) unten.</li><li>Ersetzen Sie die automatisch ausgefüllte Metrik &quot;[!UICONTROL Conversion Rate]&quot;, sodass die Aufteilung zwischen [!UICONTROL Unique visitors] durch einen positiven Metrikwert und Unique Visitors erfolgt. Siehe [Aktualisieren der Metrik &quot;Konversionsrate&quot;](#update-conversion-metric) weiter unten.</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten im Bericht [!DNL Target] übereinstimmen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

### Standardbericht des A4T-Bedienfelds - Zusätzliche Anleitungen

Die folgenden Abschnitte enthalten weitere Informationen über zusätzliche Anleitungen bei der Einrichtung Ihres standardmäßigen A4T-Bedienfeldberichts.

#### Segment erstellen {#segment}

1. Klicken Sie in der linken Leiste auf das Zeichen **&quot;+&quot;** neben **[!UICONTROL Segments]**.

   ![Pluszeichen neben Segmenten in der linken Leiste.](/help/integrations/assets/plus-sign.png)

1. Geben Sie dem Segment &quot;Besucher mit positivem Metrikwert&quot;einen Titel.
1. Wählen Sie unter &quot;**[!UICONTROL Definition]**&quot;, neben &quot;**[!UICONTROL Include]**&quot;, &quot;**[!UICONTROL Visitor]**&quot;.
1. Wählen Sie unter **[!UICONTROL Definition]** die Optimierungsmetrik in Ihrer Aktivität aus.

   Nehmen Sie in diesem Beispiel [!UICONTROL Revenue] als Optimierungsmetrik an.

1. Wählen Sie den Operator &quot;[!UICONTROL is greater than]&quot;und geben Sie dann &quot;0&quot;an.

   Diese Einstellungen werden für alle Besucher mit einem positiven Metrikwert gefiltert.

1. Klicken Sie auf **[!UICONTROL Save]**.

   ![Positiver Metrikwert](/help/integrations/assets/positive-metric-value.png)

1. Fügen Sie das neu erstellte Segment namens &quot;Besucher mit positivem Metrikwert&quot;zum A4T-Bedienfeld hinzu.
1. Ziehen Sie die Metrik [!UICONTROL Unique Visitors] in dieselbe Spalte wie die Metrik &quot;Besucher mit positivem Metrikwert&quot;.

   Diese Konfiguration erstellt ein Segment aller Unique Visitors, für die der Metrikwert positiv ist. In diesem Beispiel alle Unique Visitors, deren Umsatz größer als null war.

#### [!UICONTROL Conversion Rate] -Metrik aktualisieren {#update-conversion-metric}

1. Entfernen Sie, falls noch nicht geschehen, die vorhandene Spalte [!UICONTROL Conversion Rate] aus dem Bedienfeld, wie unten beschrieben.
1. Fügen Sie eine Metrik hinzu, indem Sie in der linken Leiste auf das &quot;+&quot;-Symbol neben dem Abschnitt &quot;**[!UICONTROL Metrics]**&quot;klicken.
1. Nennen Sie die Metrik &quot;Konversionsrate&quot;und definieren Sie sie als &quot;([!UICONTROL Unique Visitors] mit positivem Metrikwert)&quot;dividiert durch &quot;Unique Visitors&quot;, wie unten dargestellt.

   Fügen Sie das neu erstellte Segment (die unten definierten Schritte) von &quot;Besucher mit positivem Metrikwert&quot;, den Division-Operator, die Metrik &quot;Unique Visitors&quot;im Zähler und &quot;Unique Visitors&quot;als Nenner hinzu.

   ![Konversionsrate im A4T-Bedienfeld.](/help/integrations/assets/conversion-rate.png)

1. Klicken Sie auf **[!UICONTROL Save]**.

1. Ziehen Sie die neu erstellte Metrik &quot;Konversionsrate&quot;in den vorhandenen Bereich.
1. Klicken Sie auf das Zahnradsymbol und deaktivieren Sie dann das Kontrollkästchen **[!UICONTROL Percent]** , da dieser Wert zu Verwirrung führen kann.

   Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

   ![Konversionsrate individueller Besuche im A4T-Bereichsbericht](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target] definierte Konversionsrate

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Von Target ausgelöster Bericht | A4T-Bereichsbericht |
| --- | --- | --- |
| [!DNL Analytics] Berichterstellung mit [!DNL Target] Konversionsmetrik | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Steigerung beibehalten (Med).</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Confidence] -Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Behalten Sie [!UICONTROL Lift (Med)] bei.</li><li>Deaktivieren Sie die Prozentdarstellung aus der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit den Werten im Bericht [!DNL Target] übereinstimmen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

![Aktivitätskonversionen](/help/integrations/assets/optimized-table.png)

## Allgemeine Anleitung für A4T {#guidance}

Sie können zu einem vordefinierten [!UICONTROL Analytics for Target]-Bedienfeld navigieren, indem Sie auf den Link im Berichtsbildschirm in [!UICONTROL Target] klicken (dieser Link wird später in diesem Handbuch als &quot;[!DNL Target]-gesteuerter Bericht&quot;bezeichnet). Alternativ können Sie das A4T-Bedienfeld in [!DNL Analytics] erstellen (Details finden Sie weiter unten in diesem Abschnitt).

In den folgenden Abschnitten wird festgelegt, welche Konfigurationen erforderlich sind, je nachdem, welche dieser Methoden Sie auswählen. Die folgenden Schritte dienen jedoch als allgemeine Anleitung für A4T:

* Entfernen Sie die Konfidenzmetriken unabhängig von der Bereichserstellungsmethode aus dem A4T-Bedienfeld (beide sind unten beschrieben). Verweisen Sie stattdessen auf diese Werte in den [!DNL Target] -Berichten. Darüber hinaus können Aktivitätsinhaber in der Berichterstellung für [!DNL Target] identifiziert werden. Details zur Identifizierung des Aktivitätsgewinners finden Sie im Abschnitt [Identifizieren des Aktivitätsgewinners](#winner) weiter unten.
>>
* Um Verwirrung zu vermeiden, deaktivieren Sie die &quot;[!UICONTROL Percent]&quot;-Darstellung der [!UICONTROL Conversion Rate] -Metrik. Siehe [Ausblenden des Prozentsatzes aus der Spalte [!UICONTROL Conversion Rate] ](#hide-percentage) unten.
>>
* Wenn Sie ein A4T-Bedienfeld erstellen, stellen Sie sicher, dass die Datums- und Uhrzeitbereiche mit denen Ihres [!DNL Target] -Berichts übereinstimmen. Siehe [Datum und Uhrzeit im A4T-Bedienfeld ausrichten](#aligning-date-and-time) unten.

### Prozentsatz aus der Spalte [!UICONTROL Conversion Rate] ausblenden {#hide-percentage}

1. Klicken Sie auf das Symbol **Zahnrad** neben dem Titel der Spalte [!UICONTROL Conversion Rate] .

   ![Zahnradsymbol in der Spalte &quot;Konversionsrate&quot;](/help/integrations/assets/coversion-rate-gear-icon.png)

   Das Dialogfeld [!UICONTROL Column] Einstellungen wird angezeigt:

   ![Dialogfeld &quot;Spalteneinstellungen&quot;](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Percent]** .

   Ihr A4T-Bedienfeld enthält jetzt keine Prozentsätze als [!UICONTROL Conversion Rate] und stimmt mit [!DNL Target] überein, wie unten dargestellt:

   ![Spalte &quot;Konversionsrate&quot;ohne Prozentwerte](/help/integrations/assets/no-percentages.png)

### Datum und Uhrzeit im A4T-Bedienfeld ausrichten {#aligning-date-and-time}

1. Überprüfen Sie unter jedem Bedienfeld den Datumsbereich, auf den das Bedienfeld verweist, um sicherzustellen, dass der Datumsbereich mit dem Datumsbereich des Berichts [!DNL Target] übereinstimmt.

   ![Datumsbereich im A4T-Bedienfeld](/help/integrations/assets/date-range.png)

1. Legen Sie in [!DNL Analytics] den Zeitraum auf 12:00 - 23:59 Uhr fest.

### Identifizieren des Aktivitätsgewinners {#winner}

[!DNL Auto-Allocate] Aktivitätsgewinner werden ausgewählt, wenn eine Gewinnerkonversionsrate mit Konfidenzwerten größer oder gleich 95 % vorliegt. Diese Werte sollten in den [!DNL Target] -Berichten referenziert werden, da Konfidenzberechnungen die konservativeren Methoden widerspiegeln, die [!DNL Target] für [!UICONTROL Auto-Allocate] -Aktivitäten empfiehlt. Siehe [Statistische Garantien der automatischen Zuordnung](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C){target=_blank} in der *[!UICONTROL Adobe Target Business Practitioner Guide]*.

>[!NOTE]
>
Die Abzeichen &quot;Noch kein Gewinner&quot;und &quot;Gewinner&quot;sind im A4T-Bedienfeld in [!DNL Analysis Workspace] nicht verfügbar. Außerdem sollte das in den [!DNL Target] -Berichten für [!UICONTROL Auto-Allocate] -Aktivitäten angezeigte Zeichen des Gewinners &quot;Stern&quot;ignoriert werden. Siehe [Automatische Zuordnung](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa){target=_blank} in *A4T-Unterstützung für Aktivitäten mit automatischer Zuordnung und automatischem Targeting* in der *[!UICONTROL Adobe Target Business Practitioner Guide]*.

### Erstellen des A4T-Bedienfelds für [!UICONTROL Auto-Allocate] in [!DNL Analysis Workspace]

1. Um ein A4T-Bedienfeld für einen [!UICONTROL Auto-Allocate] -Aktivitätsbericht zu erstellen, beginnen Sie mit dem Bedienfeld [!UICONTROL Analytics for Target] in [!DNL Analysis Workspace] , wie unten dargestellt.

   ![Analytics for Target - Bericht &quot;Automatische Zuordnung&quot;](/help/integrations/assets/a4t-auto-allocate-report.png)

1. Führen Sie die folgenden Auswahlen aus:

   * **[!UICONTROL Control Experience]**: Wählen Sie ein beliebiges Erlebnis aus.
   * **[!UICONTROL Normalizing Metric]**: Wählen Sie **[!UICONTROL Visitors]** aus (standardmäßig im A4T-Bedienfeld enthalten). [!UICONTROL Auto-Allocate] normalisiert die Konversionsraten immer durch Unique Visitors.
   * **Erfolgsmetriken**: Wählen Sie dieselbe Metrik (Optimierung) aus, die Sie bei der Erstellung der Aktivität verwendet haben. Wenn es eine [!DNL Target] definierte Konversionsmetrik war, wählen Sie **[!UICONTROL Activity Conversion]** aus. Wählen Sie andernfalls die von Ihnen verwendete [!DNL Adobe Analytics] -Metrik aus.









