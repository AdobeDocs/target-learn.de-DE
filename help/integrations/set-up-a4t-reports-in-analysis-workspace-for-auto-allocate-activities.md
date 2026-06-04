---
title: Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!UICONTROL automatische Zuordnung]-Aktivitäten
description: Wie konfiguriere ich Berichte [!UICONTROL Analytics for Target] (A4T) in [!DNL Adobe] [!DNL Analysis Workspace] [!UICONTROL &#x200B; wenn ich &#x200B;]automatische Zuordnung“ ausführe?
role: User
level: Intermediate
topic: Personalization, Integrations
feature: Analytics for Target (A4T), Auto-Target, Integrations
doc-type: tutorial
kt: null
exl-id: 7d53adce-cc05-4754-9369-9cc1763a9450
TQID: https://experienceleague.adobe.com/5oQMgqqxw2VN-6cb29j4bwEP6VYmGRLXIp5AMJ3WWM4
product_v2:
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
feature_v2:
  - id: f7c7de77-382f-4f48-8b36-61a170f06d3d
subfeature_v2:
  - id: df62f171-ac37-440f-8f0f-f41a72ebdd34
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: c0b4abf2d4ead4d58a8db6e8970857b7b50dbe5c
workflow-type: tm+mt
source-wordcount: 1546
ht-degree: 0%

---

# Einrichten von A4T-Berichten in [!DNL Analysis Workspace] für [!DNL Auto-Allocate] Aktivitäten

Eine Aktivität [[!UICONTROL Automatische Zuordnung] &#x200B;](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/automated-traffic-allocation.html){target=_blank} in [!DNL Adobe Target] identifiziert einen Gewinner aus zwei oder mehr Erlebnissen und ordnet den Besucher-Traffic automatisch dem Gewinner zu, während der Test ausgeführt und gelernt wird. Die [!UICONTROL Analytics for Target] (A4T)-Integration für [!UICONTROL Automatische Zuordnung] ermöglicht die Anzeige von Berichtsdaten in [!DNL Adobe Analytics] und die Optimierung für benutzerdefinierte Ereignisse oder Metriken, die in [!DNL Analytics] definiert sind.

Obwohl in [!DNL Adobe Analytics] [!DNL Analysis Workspace] umfangreiche Analysefunktionen verfügbar sind, sind möglicherweise einige Änderungen am Standardbedienfeld [!UICONTROL Analytics for Target] erforderlich, um die Aktivitäten [!UICONTROL Automatische Zuordnung] korrekt zu interpretieren. Diese Änderungen sind aufgrund der Nuancen bei den [Optimierungsmetrikkriterien](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html#supported){target=_blank} erforderlich.

Jeder Optimierungstyp von -Metriken erfordert eine andere Berichtskonfiguration in A4T wie folgt:

* [!DNL Analytics] Metrik verwenden

   * [!UICONTROL Kennzahlwert pro Besucher maximieren]
   * [!UICONTROL Konversionsrate pro Unique Visitor maximieren]

* Verwenden einer [!DNL Target] Konversionsmetrik

In diesem Tutorial werden die allgemeinen Anleitungen für A4T und die kriterienspezifischen Schritte zur Konfiguration von Berichten behandelt.

## Analytics-Metriken mit Optimierungskriterien [!UICONTROL Maximieren des Metrikwerts pro &#x200B;]&quot;

**Definition**: (Gesamtmetrikwert) / ( Anzahl der Besucher)

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | [!DNL Target] Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| Kennzahlwert für eine [!DNL Analytics] Kennzahl maximieren | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Keep [!UICONTROL lift (med)].</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie [!UICONTROL &#x200B; Metrik &quot;]&quot; in „Metrik/Besucher“ um.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)] Keep [!UICONTROL Lift (Med)].</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Benennen Sie [!UICONTROL &#x200B; Metrik &quot;]&quot; in „Metrik/Besucher“ um.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

![Kennzahlwert für den Umsatz maximieren](/help/integrations/assets/maximize-metric-value-revenue.png)

## [!DNL Analytics] mit Optimierungskriterien [!UICONTROL Unique-Visitor]&quot;

**Definition**: ( Anzahl der Unique Visitors mit einem positiven Wert der Metrik) / (Gesamtzahl der Unique Visitors)

Beispiel: Angenommen, Ihre Optimierungsmetrik lautet [!UICONTROL Umsatz]. Die Aktivität enthält fünf Unique Visitors und drei dieser Unique Visitors tätigen einen Kauf. In diesem Beispiel lautet dieser Wert = (3 Besucher, für die [!UICONTROL Umsatz] positiv ist) / (5 Unique Visitors insgesamt) = 0,6 = 60 %.

>[!NOTE]
>
>Die Konversionsrate, auf die hier verwiesen wird, kann sich auf Aktionen außerhalb von Bestellungen beziehen, wie Klicks, Impressionen usw. In diesen Fällen bestünde das Kriterium weiterhin darin, die Anzahl der Besucher zu maximieren, die auf die Seite klicken bzw. sie anzeigen.

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Zielgruppengesteuerter Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| Konversionen für eine [!DNL Analytics] Metrik maximieren | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie alle drei [!UICONTROL Steigerung]-Metriken.</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie alle drei [!UICONTROL Steigerung]-Metriken.</li><li>Erstellen Sie ein Segment, um Besucher mit einem positiven Metrikwert zu filtern, die die analysierte Aktivität angesehen haben. Siehe [Erstellen eines Segments](#segment) unten.</li><li>Ersetzen Sie die automatisch ausgefüllte Metrik [!UICONTROL Konversionsrate] , sodass die Division zwischen [!UICONTROL Unique Visitors] mit einem positiven Metrikwert und Unique Visitors ist. Siehe [Aktualisieren der Konversionsratenmetrik](#update-conversion-metric) unten.</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

### Standardbericht des A4T-Bedienfelds - zusätzliche Anleitungen

In den folgenden Abschnitten finden Sie weitere Informationen zu zusätzlichen Anleitungen beim Einrichten des standardmäßigen A4T-Bedienfeldberichts.

#### Segment erstellen {#segment}

1. Klicken Sie auf das **&quot;+&quot;** neben **[!UICONTROL Segmente]** in der linken Leiste.

   ![Pluszeichen neben Segmenten in der linken Leiste.](/help/integrations/assets/plus-sign.png)

1. Geben Sie dem Segment den Titel „Besucher mit positivem Metrikwert“.
1. Wählen **[!UICONTROL unter]** neben **[!UICONTROL Einschließen]** die Option **[!UICONTROL Besucher]** aus.
1. Wählen **[!UICONTROL unter]** die Optimierungsmetrik in Ihrer Aktivität aus.

   Nehmen Sie in diesem Beispiel [!UICONTROL Umsatz] als Optimierungsmetrik an.

1. Wählen Sie den Operator &quot;[!UICONTROL ist größer als]&quot; aus und geben Sie dann „0“ an.

   Diese Einstellungen filtern nach allen Besuchern mit einem positiven Metrikwert.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Positiver Metrikwert](/help/integrations/assets/positive-metric-value.png)

1. Fügen Sie das neu erstellte Segment mit dem Namen „Besucher mit positivem Metrikwert“ zum A4T-Bedienfeld hinzu.
1. Ziehen Sie die Metrik [!UICONTROL Unique Visitors] in dieselbe Spalte wie die Spalte „Besucher mit positivem Metrikwert“.

   Diese Konfiguration erstellt ein Segment aller Unique Visitors, für die der Metrikwert positiv ist. In diesem Beispiel alle Unique Visitors, deren Umsatz größer als null war.

#### Aktualisieren der Metrik [!UICONTROL Konversionsrate] {#update-conversion-metric}

1. Entfernen Sie, falls noch nicht geschehen, die vorhandene Spalte [!UICONTROL Konversionsrate] aus dem Bedienfeld, wie unten beschrieben.
1. Fügen Sie eine Metrik hinzu, indem Sie in der linken Leiste auf das Pluszeichen **[!UICONTROL Metriken]** neben dem Abschnitt „Metriken“ klicken.
1. Benennen Sie die Metrik „Konversionsrate“ und definieren Sie sie als ([!UICONTROL Unique Visitors] mit positivem Metrikwert) dividiert durch „Unique Visitors“, wie unten dargestellt.

   Fügen Sie das neu erstellte Segment (die unten definierten Schritte) aus „Besucher mit positivem Metrikwert“, dem Divisionsoperator, der Metrik „Unique Visitors“ im Zähler und „Unique Visitors“ als Nenner hinzu.

   ![Konversionsrate im A4T-Bedienfeld.](/help/integrations/assets/conversion-rate.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**.

1. Ziehen Sie die neu erstellte Metrik „Konversionsrate“ per Drag-and-Drop in das vorhandene Bedienfeld.
1. Klicken Sie auf das Zahnradsymbol, und deaktivieren Sie **[!UICONTROL Kontrollkästchen]** Prozent), da dieser Wert zu Verwirrung führen kann.

   Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

   ![Konversionsrate pro Besuch im Bericht des A4T-Bedienfelds](/help/integrations/assets/a4t-aa-maximize-metric-value-revenue.png)

## [!DNL Target] Konversionsrate

Um den Bericht zu konfigurieren, nehmen Sie die folgenden Änderungen im A4T-Bericht vor:

| Erforderliche Änderungen | Zielgruppengesteuerter Bericht | A4T-Bedienfeldbericht |
| --- | --- | --- |
| [!DNL Analytics]-Reporting mit [!DNL Target] Konversionsmetrik | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Fahrstuhl beibehalten (Med).</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> | <ul><li>Entfernen Sie [!UICONTROL Konfidenz]-Metriken.</li><li>Entfernen Sie [!UICONTROL Lift (Low)] und [!UICONTROL Lift (High)]. Keep [!UICONTROL lift (med)].</li><li>Deaktivieren Sie die Prozentangabe in der Spalte [!UICONTROL Konversionsrate], um Verwirrung zu vermeiden. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li><li>Stellen Sie sicher, dass die Datums- und Zeitbereiche mit den Werten übereinstimmen, die Sie im [!DNL Target] sehen. Siehe [Allgemeine Anleitung für A4T](#guidance) unten.</li></ul> |

Die korrekte Konfiguration des Berichts sollte zu einem Ergebnis führen, das der folgenden Abbildung ähnelt:

![Aktivitätskonversionen](/help/integrations/assets/optimized-table.png)

## Allgemeine Leitlinien für A4T {#guidance}

Sie können zu einem vorkonfigurierten Bedienfeld [!UICONTROL Analytics for Target] navigieren, indem Sie auf den Link auf dem Berichtsbildschirm in [!UICONTROL Target] klicken (dies wird später in diesem Handbuch als &quot;[!DNL Target]-ausgelöster Bericht“ bezeichnet). Alternativ können Sie das A4T-Bedienfeld in [!DNL Analytics] erstellen (Details weiter unten in diesem Abschnitt).

In den folgenden Abschnitten wird angegeben, welche Konfigurationen erforderlich sind, je nachdem, welche dieser Methoden Sie auswählen. Die folgenden Schritte dienen jedoch als allgemeine Anleitung für A4T:

* Entfernen Sie die Konfidenzmetriken aus dem A4T-Bedienfeld, unabhängig von der Methode zur Bedienfelderstellung (beide werden unten beschrieben). Verweisen Sie stattdessen auf diese Werte in [!DNL Target] Berichten. Darüber hinaus können in [!DNL Target] Berichten Aktivitätstitel ermittelt werden, die den Zuschlag erhalten haben. Näheres zur Ermittlung des Gewinners einer Aktivität finden Sie im Abschnitt [Ermitteln des Gewinners einer Aktivität](#winner) weiter unten.
&#x200B;>>
* Um Verwirrung zu vermeiden, deaktivieren Sie die [!UICONTROL Prozent]-Darstellung der [!UICONTROL Konversionsrate]-Metrik. Siehe [Ausblenden des Prozentsatzes in der Spalte [!UICONTROL Konversionsrate] unten](#hide-percentage).
&#x200B;>>
* Wenn Sie ein A4T-Bedienfeld erstellen, stellen Sie sicher, dass die Datums- und Zeitbereiche mit denen des [!DNL Target]-Berichts übereinstimmen. Siehe [Ausrichten von Datum und Uhrzeit im A4T-Bedienfeld](#aligning-date-and-time) unten.

### Prozentwert aus der Spalte [!UICONTROL Konversionsrate] ausblenden {#hide-percentage}

1. Klicken Sie auf **Zahnradsymbol** neben dem Titel der Spalte [!UICONTROL Konversionsrate].

   ![Zahnradsymbol in der Spalte Konversionsrate](/help/integrations/assets/coversion-rate-gear-icon.png)

   Das Dialogfeld [!UICONTROL Spalten]-Einstellungen wird angezeigt:

   ![Dialogfeld „Spalteneinstellungen“](/help/integrations/assets/column-settings-dialog-box.png){width="200"}

1. Deaktivieren Sie **[!UICONTROL Kontrollkästchen]** Prozent“.

   Ihr A4T-Bedienfeld enthält jetzt keine Prozentsätze als [!UICONTROL Konversionsrate] und stimmt mit [!DNL Target] überein, wie unten dargestellt:

   ![Die Spalte Konversionsrate zeigt keine Prozentsätze an](/help/integrations/assets/no-percentages.png)

### Ausrichten von Datum und Uhrzeit im A4T-Bedienfeld {#aligning-date-and-time}

1. Überprüfen Sie unter jedem Bedienfeld den Datumsbereich, auf den das Bedienfeld verweist, um sicherzustellen, dass der Datumsbereich mit dem [!DNL Target] Bericht übereinstimmt.

   ![Datumsbereich im A4T-Bedienfeld](/help/integrations/assets/date-range.png)

1. Stellen Sie [!DNL Analytics] den Zeitbereich auf 12:00am bis 11:59pm ein.

### Ermitteln des Aktivitätsiegers {#winner}

[!DNL Auto-Allocate] Aktivitätsgewinner werden ausgewählt, wenn eine erfolgreichste Konversionsrate mit Konfidenzwerten größer oder gleich 95 % vorliegt. Diese Werte sollten in den [!DNL Target]-Berichten referenziert werden, da Konfidenzberechnungen die konservativeren Methoden widerspiegeln, die [!DNL Target] für Aktivitäten [!UICONTROL Automatische Zuordnung] empfiehlt. Siehe [Statistische Garantien der automatischen Zuordnung](https://experienceleague.adobe.com/docs/target/using/activities/auto-allocate/determine-winner.html#section_7AF3B93E90BA4B80BC9FC4783B6A389C){target=_blank} im *[!UICONTROL Handbuch für Adobe Target Business Practices]*.

>[!NOTE]
>
>Die Abzeichen „Noch kein Gewinner“ und „Gewinner“ sind im A4T-Bedienfeld in [!DNL Analysis Workspace] nicht verfügbar. Außerdem sollte das Gewinner-Abzeichen „Stern“ ignoriert werden, das in [!DNL Target] Berichten für [!UICONTROL Automatische Zuordnung]-Aktivitäten angezeigt wird. Siehe [Automatische Zuordnung](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t-at-aa.html?lang=en#aa){target=_blank} in *A4T-Unterstützung für automatische Zuordnungs- und automatische Targeting-* im *[!UICONTROL Handbuch für Adobe Target Business Practices]*.

### Erstellen des Bedienfelds „A4T“ für [!UICONTROL Automatische Zuordnung] in [!DNL Analysis Workspace]

1. Um ein A4T-Bedienfeld für einen [!UICONTROL Automatische Zuordnung] Aktivitätsbericht zu erstellen, beginnen Sie mit dem Bedienfeld [!UICONTROL Analytics for Target] in [!DNL Analysis Workspace], wie unten dargestellt.

   ![Analytics for Target - Bericht zur automatischen Zuordnung](/help/integrations/assets/a4t-auto-allocate-report.png)

1. Nehmen Sie die folgenden Auswahlen vor:

   * **[!UICONTROL Kontrollerlebnis]**: Wählen Sie ein Erlebnis aus.
   * **[!UICONTROL Normalisierungsmetrik]**: Wählen Sie **[!UICONTROL Besucher]** aus (standardmäßig im A4T-Bedienfeld enthalten). [!UICONTROL Automatische Zuordnung] normalisiert Konversionsraten immer für Unique Visitors.
   * **Erfolgsmetriken**: Wählen Sie dieselbe (Optimierungs-)Metrik aus, die Sie bei der Erstellung der Aktivität verwendet haben. Wenn es sich um eine [!DNL Target] Konversionsmetrik handelte, wählen Sie **[!UICONTROL Aktivitätskonversion]** aus. Wählen Sie andernfalls die verwendete [!DNL Adobe Analytics] aus.









