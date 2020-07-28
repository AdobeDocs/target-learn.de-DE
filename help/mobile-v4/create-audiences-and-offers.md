---
title: Audiencen und Angebot in Adobe Target erstellen
seo-title: Audiencen und Angebot in Adobe Target erstellen
description: 'In dieser Lektion werden wir Audiencen und Angebote in Adobe Target für die drei Orte bauen, die wir in den vorherigen Lektionen implementiert haben. Diese werden verwendet, um personalisierte Erlebnisse in der nächsten Lektion anzuzeigen.   '
seo-description: In dieser Lektion werden wir Audiencen und Angebote in Adobe Target für die drei Orte bauen, die wir in den vorherigen Lektionen implementiert haben. Diese werden verwendet, um personalisierte Erlebnisse in der nächsten Lektion anzuzeigen.
feature: mobile
kt: 3040
audience: developer
doc-type: tutorial
activity-type: implement
translation-type: tm+mt
source-git-commit: 199fbde58696a0511623c5500cc6afbbcfdd67a3
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 1%

---


# Audiencen und Angebot in Adobe Target erstellen

In dieser Lektion gehen wir in die [!DNL Target] Oberfläche und bauen Audiencen und Angebote für die drei Orte, die wir in den vorherigen Lektionen implementiert haben.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Zielgruppen in Adobe Target
* Erstellen von Angeboten in Adobe Target

In dieser Lektion werden wir Audiencen und Angebot erstellen, die erforderlich sind, um die zu Beginn des Tutorials definierten Anwendungsfälle für die Personalisierung zu realisieren. Wir möchten die Bildschirme &quot;Start&quot;und &quot;Suche&quot;verwenden, um App-Benutzern bei der Buchung ihrer Reisen zu helfen, und wir möchten den Bildschirm &quot;Vielen Dank&quot;verwenden, um einige relevante Promotions basierend auf dem Ziel des Benutzers anzuzeigen. Die folgende Tabelle zeigt, was wir in dieser Lektion für jeden Ort aufbauen werden:

| Position | Zielgruppe | Angebot |
| --- | --- | --- |
| wetravel_engagement_home | Neue Mobile App-Benutzer | &quot;Wählen Sie Ihre Herkunft und Ihr Ziel aus, um nach verfügbaren Buslinien zu suchen.&quot; |
| wetravel_engagement_search | Neue Mobile App-Benutzer | &quot;Verwenden Sie Filter, um Ihre Suchergebnisse einzugrenzen&quot; |
| wetravel_engagement_home | Wiederkehrende Benutzer mobiler Apps | &quot;Willkommen zurück! Verwenden Sie den Promo-Code BACK30 während des Kassengangs, um einen Rabatt von 10 % zu erhalten.&quot; |
| wetravel_engagement_search | Wiederkehrende Benutzer mobiler Apps | Standardinhalt |
| wetravel_context_dest | Ziel: San Diego | &quot;DJ&quot; |
| wetravel_context_dest | Ziel: Los Angeles | &quot;Universal&quot; |

## Arbeitsbereich auswählen

Wenn Ihre Firma mithilfe von &quot;Eigenschaften&quot;und &quot;Arbeitsbereiche&quot;Begrenzungen für die Personalisierung von Apps und Websites festlegt und Sie den Parameter &quot;at_property&quot;in der letzten Lektion implementiert haben, sollten Sie zunächst sicherstellen, dass Sie sich im richtigen Arbeitsbereich befinden, bevor Sie mit dieser Lektion fortfahren. Wenn Sie keine Eigenschaften und Arbeitsbereiche verwenden, ignorieren Sie diesen Schritt einfach. Wählen Sie den Arbeitsbereich aus, den Sie in der vorherigen Lektion verwendet haben, um den Wert at_property zu kopieren:

![Arbeitsflächenbeispiel](assets/workspace.jpg)

## Audiencen erstellen

Erstellen wir nun die Audiencen, die wir zur Personalisierung der App verwenden werden.

### Audience für neue Benutzer erstellen

Mithilfe von Adobe Target-Audiencen werden bestimmte Gruppen von Besuchern identifiziert. Angebot können dann auf diese spezifischen Gruppen ausgerichtet werden. Für die ersten beiden Standorte verwenden wir eine Audience &quot;Neue Benutzer&quot;:

1. Klicken Sie in der oberen Navigation auf **[!UICONTROL Audiencen]** .
1. Click the **[!UICONTROL Create Audience]** button.
   ![Neue Audience erstellen](assets/audience_new_mobile_app_users_1.jpg)

1. Geben Sie **[!UICONTROL Neue Mobilanwendungsbenutzer]** als Audience ein.
1. Wählen Sie **[!UICONTROL Hinzufügen Regel]**.
1. Wählen Sie eine **[!UICONTROL benutzerspezifische]** Regel.
   ![Neue Audience erstellen](assets/audience_new_mobile_app_users_2.jpg)

1. Wählen Sie **[!UICONTROL a.Launches]**.
1. Select **[!UICONTROL is less than]**.
1. Enter **5**.
1. Speichern Sie die neue Audience.
   ![Neue Audience erstellen](assets/audience_new_mobile_app_users_3.jpg)

### Audience für wiederkehrende Benutzer erstellen

Gehen Sie wie oben beschrieben vor, um eine Audience für wiederkehrende Benutzer zu erstellen.

1. Benennen Sie die Audience _rückkehrende Mobilanwendungsbenutzer_.
1. Verwenden Sie **[!UICONTROL a.Launches ist größer als oder gleich 5]** als benutzerspezifische Regel.
1. Speichern Sie die neue Audience.

   ![Eine wiederkehrende Audience erstellen](assets/audience_returning_mobile_app_users.jpg)

>[!NOTE]
>
>Alle Lebenszyklusmetriken und -dimensionen, die im [!DNL Target] mobilen SDK erfasst werden, erhalten den Präfix &quot;a&quot;(z. B. a.Launches) und stehen im Dropdown-Menü unter &quot;Benutzerdefiniert&quot;zur Verfügung und können zum Erstellen von Audiencen verwendet werden.

### Audience für Benutzer erstellen, die eine Reise nach San Diego buchen

Als Nächstes erstellen wir einige Audiencen für einige der Reiseziele, die von der App We.Travel angeboten werden. In der letzten Lektion haben wir das Ziel als Positionsparameter in der Ortsanforderung &quot;wetravel_context_dest&quot;übergeben. Dieser Parameter ist in der Option &quot;Benutzerdefiniert&quot;des Dropdown-Menüs verfügbar.

>[!NOTE]
>
>Wenn ein Parameter, den Sie im Dropdown-Menü Benutzerdefiniert erwarten, nicht auf der [!DNL Target] Oberfläche angezeigt wird, überprüfen Sie bei der Dublette, ob er tatsächlich in der Anforderung übergeben wird. Wenn Sie sich vergewissert haben, dass der Parameter in der Anforderung enthalten ist, jedoch nicht verzögert in die [!DNL Target] Oberfläche geladen wurde, können Sie einfach den Parameternamen eingeben und die Eingabetaste drücken, um die Audience weiter zu definieren

1. Benennen Sie die _Zieladresse der Audience: San Diego_.
1. Verwenden Sie eine benutzerspezifische Regel mit dieser Definition: _locationDest enthält San Diego_.
1. Speichern Sie die neue Audience.

   ![Audience &quot;San Diego&quot;erstellen](assets/audience_locationDest_san_diego.jpg)

### Audience für Benutzer erstellen, die eine Reise nach Los Angeles buchen

1. Benennen Sie die _Zieladresse der Audience: Los Angeles_
1. Verwenden Sie eine benutzerspezifische Regel mit dieser Definition: _locationDest enthält Los Angeles_
1. Speichern Sie die neue Audience.

![&quot;Los Angeles&quot;-Audience erstellen](assets/audience_locationDest_los_angeles.jpg)

## Erstellen von Angeboten

Nun, lassen Sie uns Angebote erstellen, um diese Nachrichten anzuzeigen. Zur Erinnerung: Angebot sind Codefragmente/Inhaltselemente, die in der [!DNL Target] Antwort bereitgestellt werden. Sie werden meist auf der [!DNL Target] Benutzeroberfläche erstellt, können aber auch über die API oder die Experience Fragments-Integration mit Adobe Experience Manager erstellt werden. In mobilen Apps sind JSON-Angebot häufig. In diesem Lernprogramm verwenden wir HTML-Angebot, die verwendet werden können, um Klartext-Inhalte (einschließlich JSON) in die App zu übertragen.

### Angebot für neue Benutzer erstellen

Erstellen Sie zunächst Angebote für die Nachrichten an neue Benutzer:

1. Klicken Sie in der oberen Navigation auf **[!UICONTROL Angebot]** .
1. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Wählen Sie **[!UICONTROL HTML-Angebot]**.

   ![Startseite erstellen, Angebot](assets/offer_home_1.jpg)

1. Benennen Sie das Angebot _Home: Neue Benutzer_ einbinden.
1. Geben Sie Quelle und Ziel _auswählen ein, um nach verfügbaren Bussen_ als Code zu suchen.
1. Speichern Sie das neue Angebot.

   ![HTML-Angebot für die Startseite erstellen](assets/offer_home_2.jpg)

### Angebot für wiederkehrende Benutzer erstellen

Erstellen wir nun ein Angebot für wiederkehrende Benutzer (das zweite Angebot ist Standardinhalt, der als nichts angezeigt wird):

1. Benennen Sie das Angebot _Home: Wiederkehrende Benutzer_.
1. Geben Sie _Willkommen zurück! Verwenden Sie den Promo-Code BACK30 während des Kassengangs, um einen Rabatt von 10% zu erhalten._ als HTML-Code.
1. Speichern Sie das neue Angebot.

   ![HTML-Angebot für die Startseite erstellen](assets/offer_home_returning_users.jpg)

### San Diego-Angebot erstellen

Wenn &quot;DJ&quot;an die Dankeschön-Aktivität zurückgegeben wird, zeigt die Logik in der Funktion filterRecommendationBasedOnOffer() ein Banner für &quot;Rock Night with DJ SAM&quot;an:

1. Benennen Sie das Angebot _Promotion für San Diego_.
1. Geben Sie _DJ_ als HTML-Code ein.
1. Speichern Sie das neue Angebot.

![Angebot &quot;San Diego&quot;erstellen](assets/offer_san_diego.jpg)

### Angebot für Benutzer erstellen, die nach Los Angeles gehen

Wenn &quot;Universal&quot;an die Danksagungsfunktion zurückgegeben wird, zeigt die Logik in der Funktion filterRecommendationBasedOnOffer() ein Banner für &quot;Universal Studios&quot;an:

1. Benennen Sie das Angebot _Promotion für Los Angeles_.
1. Geben Sie _Universal_ als HTML-Code ein.
1. Speichern Sie das neue Angebot.

![Angebot &quot;Los Angeles&quot;erstellen](assets/offer_los_angeles.jpg)

## Schlussfolgerung 

Jetzt haben wir unsere Audiencen und Angebote. In der nächsten Lektion erstellen wir Aktivitäten, die Orte, Audiencen und Angebot miteinander verbinden, um personalisierte Erlebnisse zu schaffen!

**[NÄCHSTES: &quot;Layouts personalisieren&quot;>](personalize-layouts.md)**
