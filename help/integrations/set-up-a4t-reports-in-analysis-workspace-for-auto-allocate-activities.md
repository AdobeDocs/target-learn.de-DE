---
title: Einrichten von A4T-Berichten in  [!DNL Analysis Workspace]  für [!UICONTROL Auto-Allocate] Aktivitäten
description: Wie konfiguriere ich [!UICONTROL Analytics for Target] (A4T)-Berichte in [!DNL Adobe] [!DNL Analysis Workspace] wenn ich [!UICONTROL Auto-Allocate]-Aktivitäten ausführe?
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

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Allocate] Aktivitäten

Eine [[!UICONTROL Auto-Allocate] Aktivität](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html){target=_blank} in [!DNL Adobe Target] identifiziert einen Gewinner aus zwei oder mehr Erlebnissen und ordnet den Besucher-Traffic automatisch dem Gewinner zu, während der Test ausgeführt und gelernt wird. Mit der [!UICONTROL Analytics for Target] (A4T)-Integration für [!UICONTROL Auto-Allocate] können Sie Berichtsdaten in [!DNL Adobe Analytics] anzeigen. Außerdem können Sie sie für benutzerdefinierte Ereignisse oder Metriken optimieren, die in [!DNL Analytics] definiert sind.

Obwohl in [!DNL Adobe Analytics] [!DNL Analysis Workspace] umfangreiche Analysefunktionen verfügbar sind, sind möglicherweise einige Änderungen am [!UICONTROL Analytics for Target] erforderlich, um [!UICONTROL Auto-Allocate] Aktivitäten korrekt zu interpretieren. Diese Änderungen sind aufgrund der Nuancen bei den [Optimierungsmetrikkriterien](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank} erforderlich.

Jeder Optimierungstyp von -Metriken erfordert eine andere Berichtskonfiguration in A4T wie folgt:

* [!DNL Analytics] Metrik verwenden

   * [!UICONTROL Maximize metric value per visitor]
   * [!UICONTROL Maximize unique visitor conversion rate]

* Verwenden einer [!DNL Target] Konversionsmetrik

In diesem Tutorial werden die allgemeinen Anleitungen für A4T und die kriterienspezifischen Schritte zur Konfiguration von Berichten behandelt.

## Analytics-Metriken mit Optimierungskriterien &quot;[!UICONTROL Maximize Metric Value Per Visitor]&quot;

**Definition**: (Gesamtmetrikwert) / ( Anzahl der Besucher)

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | [!DNL Target] Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| Kennzahlwert für eine [!DNL Analytics] Kennzahl maximieren | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>[!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] entfernen. Bleib [!UICONTROL Lift (Med)].</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie die [!UICONTROL Conversion] in „Metrik/Besucher“ um.</li></ul> | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] Sie [!UICONTROL Lift (Med)].</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie die [!UICONTROL Conversion] in „Metrik/Besucher“ um.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

![Kennzahlwert für den Umsatz maximieren](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] von Metriken mit Optimierungskriterien &quot;[!UICONTROL Unique Visitor Conversion Rate]&quot;

**Definition**: ( Anzahl der Unique Visitors mit einem positiven Wert der Metrik) / (Gesamtzahl der Unique Visitors)

Beispiel: Angenommen, Ihre Optimierungsmetrik ist [!UICONTROL Revenue]. Die Aktivität enthält fünf Unique Visitors und drei dieser Unique Visitors tätigen einen Kauf. In diesem Beispiel lautet dieser Wert = (3 Besucher, für die [!UICONTROL Revenue] positiv ist) / (5 Unique Visitors insgesamt) = 0,6 = 60 %.

>[!NOTE]
>
>Die Konversionsrate, auf die hier verwiesen wird, kann sich auf Aktionen außerhalb von Bestellungen beziehen, wie Klicks, Impressionen usw. In diesen Fällen bestünde das Kriterium weiterhin darin, die Anzahl der Besucher zu maximieren, die auf die Seite klicken bzw. sie anzeigen.

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Zielgruppengesteuerter Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| Konversionen für eine [!DNL Analytics] Metrik maximieren | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>Entfernen Sie alle drei [!UICONTROL Lift].</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>Entfernen Sie alle drei [!UICONTROL Lift].</li><li>Erstellen Sie ein Segment, um Besucher mit einem positiven Metrikwert zu filtern, die die analysierte Aktivität angesehen haben. Siehe [Erstellen eines Segments](#segment) unten.</li><li>Ersetzen Sie die automatisch ausgefüllte [!UICONTROL Conversion Rate]-Metrik, sodass die Division zwischen [!UICONTROL Unique visitors] mit einem positiven Metrikwert und Unique Visitors ist. Siehe [Aktualisieren der Konversionsratenmetrik](#update-conversion-metric) unten.</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

### Standardbericht des A4T-Bedienfelds - zusätzliche Anleitungen

In den folgenden Abschnitten finden Sie weitere Informationen zu zusätzlichen Anleitungen beim Einrichten des standardmäßigen A4T-Bedienfeldberichts.

#### Segment erstellen {#segment}

1. Klicken Sie auf das **&quot;+&quot;** neben **[!UICONTROL Segments]** in der linken Leiste.

   ![Pluszeichen neben Segmenten in der linken Leiste.](/help/integrations/assets/plus-sign.png)

1. Geben Sie dem Segment den Titel „Besucher mit positivem Metrikwert“.
1. Klicken Sie unter **[!UICONTROL Definition]** neben **[!UICONTROL Include]** auf **[!UICONTROL Visitor]**.
1. Wählen Sie unter **[!UICONTROL Definition]** die Optimierungsmetrik in Ihrer Aktivität aus.

   Nehmen wir in diesem Beispiel [!UICONTROL Revenue] als Optimierungsmetrik an.

1. Wählen Sie den Operator &quot;[!UICONTROL is greater than]&quot; aus und geben Sie dann „0“ an.

   Diese Einstellungen filtern nach allen Besuchern mit einem positiven Metrikwert.

1. Klicken Sie auf **[!UICONTROL Save]**.

   ![Positiver Metrikwert](/help/integrations/assets/positive-metric-value.png)

1. Fügen Sie das neu erstellte Segment mit dem Namen „Besucher mit positivem Metrikwert“ zum A4T-Bedienfeld hinzu.
1. Ziehen Sie die [!UICONTROL Unique Visitors] Metrik per Drag-and-Drop in dieselbe Spalte wie die „Besucher mit positivem Metrikwert“.

   Diese Konfiguration erstellt ein Segment aller Unique Visitors, für die der Metrikwert positiv ist. In diesem Beispiel alle Unique Visitors, deren Umsatz größer als null war.

#### [!UICONTROL Conversion Rate] aktualisieren {#update-conversion-metric}

1. Wenn Sie dies noch nicht getan haben, entfernen Sie die vorhandene Spalte [!UICONTROL Conversion Rate] aus dem Bedienfeld, wie unten beschrieben.
1. Fügen Sie eine Metrik hinzu, indem Sie auf das Pluszeichen (+) neben dem Abschnitt **[!UICONTROL Metrics]** in der linken Leiste klicken.
1. Benennen Sie die Metrik „Konversionsrate“ und definieren Sie sie als „([!UICONTROL Unique Visitors] mit positivem Metrikwert)“ dividiert durch „Unique Visitors“, wie unten dargestellt.

   Fügen Sie das neu erstellte Segment (die unten definierten Schritte) aus „Besucher mit positivem Metrikwert“, dem Divisionsoperator, der Metrik „Unique Visitors“ im Zähler und „Unique Visitors“ als Nenner hinzu.

   ![Konversionsrate im A4T-Bedienfeld.](/help/integrations/assets/conversion-rate.png)

1. Klicken Sie auf **[!UICONTROL Save]**.

1. Ziehen Sie die neu erstellte Metrik „Konversionsrate“ per Drag-and-Drop in das vorhandene Bedienfeld.
1. Klicken Sie auf das Zahnradsymbol und deaktivieren Sie dann das Kontrollkästchen **[!UICONTROL Percent]**, da dieser Wert zu Verwirrung führen kann.

   Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

   ![Konversionsrate pro Besuch im Bericht des A4T-Bedienfelds](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target] Konversionsrate

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Zielgruppengesteuerter Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| [!DNL Analytics]-Reporting mit [!DNL Target] Konversionsmetrik | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>[!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] entfernen. Fahrstuhl beibehalten (Med).</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>[!UICONTROL Confidence] entfernen.</li><li>[!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] entfernen. Bleib [!UICONTROL Lift (Med)].</li><li>Deaktivieren Sie die prozentuale Darstellung in der Spalte [!UICONTROL Conversion Rate] , um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

![Aktivitätskonversionen](/help/integrations/assets/optimized-table.png)

## Allgemeine Leitlinien für A4T {#guidance}

Sie können zu einem vorkonfigurierten [!UICONTROL Analytics for Target] navigieren, indem Sie auf den Link im Berichtsbildschirm in [!UICONTROL Target] klicken (dies wird später in diesem Handbuch als &quot;[!DNL Target] Bericht“ bezeichnet). Alternativ können Sie das A4T-Bedienfeld in [!DNL Analytics] erstellen (Details weiter unten in diesem Abschnitt).

In den folgenden Abschnitten wird angegeben, welche Konfigurationen erforderlich sind, je nachdem, welche dieser Methoden Sie auswählen. Die folgenden Schritte dienen jedoch als allgemeine Anleitung für A4T:

* Entfernen Sie die Konfidenzmetriken aus dem A4T-Bedienfeld, unabhängig von der Methode zur Bedienfelderstellung (beide werden unten beschrieben). Verweisen Sie stattdessen auf diese Werte in [!DNL Target] Berichten. Darüber hinaus können in [!DNL Target] Berichten Aktivitätstitel ermittelt werden, die den Zuschlag erhalten haben. Näheres zur Ermittlung des Gewinners einer Aktivität finden Sie im Abschnitt [Ermitteln des Gewinners einer Aktivität](#winner) weiter unten.
&#x200B;>>
* Um Verwirrung zu vermeiden, deaktivieren Sie die Darstellung &quot;[!UICONTROL Percent]&quot; der [!UICONTROL Conversion Rate]. Siehe [Prozentsatz in der [!UICONTROL Conversion Rate] Spalte ausblenden](#hide-percentage) unten.
&#x200B;>>
* Wenn Sie ein A4T-Bedienfeld erstellen, stellen Sie sicher, dass die Datums- und Zeitbereiche mit denen des [!DNL Target]-Berichts übereinstimmen. Siehe [Ausrichten von Datum und Uhrzeit im A4T-Bedienfeld](#aligning-date-and-time) unten.

### Prozentwert aus der [!UICONTROL Conversion Rate] Spalte ausblenden {#hide-percentage}

1. Klicken Sie auf **Zahnrad**-Symbol neben dem Titel der [!UICONTROL Conversion Rate] Spalte.

   ![Zahnradsymbol in der Spalte Konversionsrate](/help/integrations/assets/coversion-rate-gear-icon.png)

   Das Dialogfeld [!UICONTROL Column] wird angezeigt:

   ![Dialogfeld „Spalteneinstellungen“](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Deaktivieren Sie das Kontrollkästchen **[!UICONTROL Percent]** .

   Ihr A4T-Bedienfeld enthält jetzt keine Prozentsätze mehr als [!UICONTROL Conversion Rate] und stimmt [!DNL Target] überein, wie unten dargestellt:

   ![Die Spalte Konversionsrate zeigt keine Prozentsätze an](/help/integrations/assets/no-percentages.png)

### Ausrichten von Datum und Uhrzeit im A4T-Bedienfeld {#aligning-date-and-time}

1. Überprüfen Sie unter jedem Bedienfeld den Datumsbereich, auf den das Bedienfeld verweist, um sicherzustellen, dass der Datumsbereich mit dem [!DNL Target] Bericht übereinstimmt.

   ![Datumsbereich im A4T-Bedienfeld](/help/integrations/assets/date-range.png)

1. Stellen Sie [!DNL Analytics] den Zeitbereich auf 12:00 bis 23:59 Uhr ein.

### Ermitteln des Aktivitätsiegers {#winner}

[!DNL Auto-Allocate] Aktivitätsgewinner werden ausgewählt, wenn eine erfolgreichste Konversionsrate mit Konfidenzwerten größer oder gleich 95 % vorliegt. Diese Werte sollten in den [!DNL Target]-Berichten referenziert werden, da Konfidenzberechnungen die konservativeren Methoden widerspiegeln, die [!DNL Target] für [!UICONTROL Auto-Allocate] Aktivitäten empfiehlt. Siehe [Statistische Garantien der automatischen Zuordnung](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C){target=_blank} im *[!UICONTROL Adobe Target Business Practitioner Guide]*.

>[!NOTE]
>
>Die Abzeichen „Noch kein Gewinner“ und „Gewinner“ sind im A4T-Bedienfeld in [!DNL Analysis Workspace] nicht verfügbar. Außerdem sollte das in [!DNL Target] Berichten für [!UICONTROL Auto-Allocate] Aktivitäten angezeigte Gewinner-Abzeichen „Stern“ ignoriert werden. Siehe [Automatische Zuordnung](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa){target=_blank} in *A4T-Unterstützung für automatische Zuordnungs- und automatische Targeting-* in der *[!UICONTROL Adobe Target Business Practitioner Guide]*.

### Erstellen des Bedienfelds „A4T“ für [!UICONTROL Auto-Allocate] in [!DNL Analysis Workspace]

1. Um ein A4T-Bedienfeld für einen [!UICONTROL Auto-Allocate] Aktivitätsbericht zu erstellen, beginnen Sie mit dem [!UICONTROL Analytics for Target] Bedienfeld in [!DNL Analysis Workspace], wie unten dargestellt.

   ![Analytics for Target - Bericht zur automatischen Zuordnung](/help/integrations/assets/a4t-auto-allocate-report.png)

1. Nehmen Sie die folgenden Auswahlen vor:

   * **[!UICONTROL Control Experience]**: Beliebiges Erlebnis auswählen.
   * **[!UICONTROL Normalizing Metric]**: Wählen Sie **[!UICONTROL Visitors]** aus (standardmäßig im A4T-Bedienfeld enthalten). [!UICONTROL Auto-Allocate] normalisiert Konversionsraten von Unique Visitors immer.
   * **Erfolgsmetriken**: Wählen Sie dieselbe (Optimierungs-)Metrik aus, die Sie bei der Erstellung der Aktivität verwendet haben. Wenn es sich um eine [!DNL Target] Konversionsmetrik handelte, wählen Sie **[!UICONTROL Activity Conversion]**. Wählen Sie andernfalls die verwendete [!DNL Adobe Analytics] aus.









