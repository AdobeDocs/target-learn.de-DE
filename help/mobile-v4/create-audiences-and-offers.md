---
title: Erstellen von Zielgruppen und Angeboten in Adobe Target
description: 'In dieser Lektion erstellen wir in Adobe Target Zielgruppen und Angebote für die drei Orte, die wir in den vorherigen Lektionen implementiert haben. Diese werden verwendet, um in der nächsten Lektion personalisierte Erlebnisse anzuzeigen.   '
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 4b153e4f-a979-49a8-8c26-f7ac95162a2f
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 1%

---

# Erstellen von Zielgruppen und Angeboten in Adobe Target

In dieser Lektion gehen wir in die [!DNL Target]-Schnittstelle und erstellen Audiences und Angebote für die drei Orte, die wir in den vorherigen Lektionen implementiert haben.

## Lernziele

Am Ende dieser Lektion können Sie:

* Erstellen von Zielgruppen in Adobe Target
* Angebote in Adobe Target erstellen

In dieser Lektion erstellen wir Audiences und Angebote, die für die am Anfang des Tutorials definierten Anwendungsfälle der Personalisierung erforderlich sind. Wir möchten die Bildschirme &quot;Startseite&quot;und &quot;Suche&quot;verwenden, um App-Benutzer bei der Buchung ihrer Reisen zu unterstützen. Außerdem möchten wir den Dankesbildschirm verwenden, um einige relevante Promotions basierend auf dem Ziel des Benutzers anzuzeigen. Hier finden Sie eine Tabelle, die zeigt, was wir in dieser Lektion für jeden Ort erstellen werden:

| Standort | Zielgruppe | Angebot |
| --- | --- | --- |
| wetravel_engage_home | Neue Mobile App-Benutzer | &quot;Wählen Sie Ihren Ursprung und Ihr Ziel aus, um nach verfügbaren Busrouten zu suchen&quot; |
| wetravel_engage_search | Neue Mobile App-Benutzer | &quot;Verwenden Sie Filter, um Ihre Suchergebnisse einzugrenzen&quot; |
| wetravel_engage_home | Zurückgeben von App-Benutzern | &quot;Willkommen zurück! Verwenden Sie den Promo-Code BACK30 während des Checkout, um einen 10-%-Rabatt zu erhalten.&quot; |
| wetravel_engage_search | Zurückgeben von App-Benutzern | Standardinhalt |
| wetravel_context_dest | Ziel: San Diego | &quot;DJ&quot; |
| wetravel_context_dest | Ziel: Los Angeles | &quot;Universal&quot; |

## Arbeitsbereich auswählen

Wenn Ihr Unternehmen mithilfe von Eigenschaften und Arbeitsbereichen Grenzen für die Personalisierung von Apps und Websites festlegt und Sie den Parameter at_property in der letzten Lektion implementiert haben, sollten Sie zunächst sicherstellen, dass Sie sich im richtigen Arbeitsbereich befinden, bevor Sie mit dieser Lektion fortfahren. Wenn Sie Eigenschaften und Arbeitsbereiche nicht verwenden, ignorieren Sie diesen Schritt. Wählen Sie den Arbeitsbereich aus, den Sie in der vorherigen Lektion verwendet haben, um den Wert at_property zu kopieren:

![Arbeitsbereichsbeispiel](assets/workspace.jpg)

## Erstellen von Zielgruppen

Erstellen wir nun die Zielgruppen, mit denen wir die App personalisieren.

### Erstellen einer Zielgruppe für neue Benutzer

Adobe Target-Zielgruppen werden verwendet, um bestimmte Besuchergruppen zu identifizieren. Angebote können dann auf bestimmte Gruppen ausgerichtet werden. Für die ersten beiden Orte wird eine Zielgruppe &quot;Neue Benutzer&quot;verwendet:

1. Klicken Sie in der oberen Navigation auf **[!UICONTROL Zielgruppen]** .
1. Klicken Sie auf die Schaltfläche **[!UICONTROL Zielgruppe erstellen]** .
   ![Neue Zielgruppe erstellen](assets/audience_new_mobile_app_users_1.jpg)

1. Geben Sie **[!UICONTROL Neue Mobile App-Benutzer]** als Zielgruppennamen ein.
1. Wählen Sie **[!UICONTROL Regel hinzufügen]** aus.
1. Wählen Sie eine Regel **[!UICONTROL Benutzerdefiniert]** aus.
   ![Neue Zielgruppe erstellen](assets/audience_new_mobile_app_users_2.jpg)

1. Wählen Sie **[!UICONTROL a.Launches]** aus.
1. Wählen Sie **[!UICONTROL ist kleiner als]** aus.
1. Geben Sie **5** ein.
1. Speichern Sie die neue Zielgruppe.
   ![Neue Zielgruppe erstellen](assets/audience_new_mobile_app_users_3.jpg)

### Erstellen einer Zielgruppe für wiederkehrende Benutzer

Führen Sie die oben aufgeführten Schritte aus, um eine Zielgruppe für wiederkehrende Benutzer zu erstellen.

1. Nennen Sie die Zielgruppe _Returning Mobile App Users_.
1. Verwenden Sie **[!UICONTROL a.Launches größer oder gleich 5]** als benutzerdefinierte Regel.
1. Speichern Sie die neue Zielgruppe.

   ![Erstellen einer wiederkehrenden Zielgruppe](assets/audience_returning_mobile_app_users.jpg)

>[!NOTE]
>
>Alle Lebenszyklusmetriken und -dimensionen, die im mobilen SDK [!DNL Target] erfasst werden, erhalten das Präfix &quot;a&quot;(z. B. a.Launches). Sie sind in der Option &quot;Benutzerdefiniert&quot;des Dropdown-Menüs verfügbar und können zum Erstellen von Zielgruppen verwendet werden.

### Erstellen einer Zielgruppe für Benutzer, die eine Reise nach San Diego buchen

Als Nächstes erstellen wir einige Zielgruppen für einige der Ziele, die von der We.Travel-App angeboten werden. In der letzten Lektion haben wir das Ziel als Positionsparameter in der Ortsanforderung &quot;wetravel_context_dest&quot;übergeben. Dieser Parameter ist in der Option &quot;Benutzerdefiniert&quot;des Dropdown-Menüs verfügbar.

>[!NOTE]
>
>Wenn ein Parameter, den Sie im Dropdown-Menü &quot;Benutzerdefiniert&quot;erwarten, nicht in der [!DNL Target]-Benutzeroberfläche angezeigt wird, überprüfen Sie, ob er tatsächlich in der Anfrage übergeben wird. Wenn Sie überprüft haben, ob sich in der Anfrage befindet, aber nicht verzögert in die [!DNL Target]-Schnittstelle geladen wurde, können Sie einfach den Parameternamen eingeben und die Eingabetaste drücken, um die Audience weiter zu definieren

1. Benennen Sie die Audience _Ziel: San Diego_.
1. Verwenden Sie eine benutzerdefinierte Regel mit dieser Definition: _locationDest enthält San Diego_.
1. Speichern Sie die neue Zielgruppe.

   ![Zielgruppe &quot;San Diego&quot;erstellen](assets/audience_locationDest_san_diego.jpg)

### Erstellen einer Audience für Benutzer, die eine Reise nach Los Angeles buchen

1. Benennen Sie die Audience _Ziel: Los Angeles_
1. Verwenden Sie eine benutzerdefinierte Regel mit dieser Definition: _locationDest enthält Los Angeles_
1. Speichern Sie die neue Zielgruppe.

![&quot;Los Angeles&quot;-Zielgruppe erstellen](assets/audience_locationDest_los_angeles.jpg)

## Erstellen von Angeboten

Erstellen wir nun Angebote zur Anzeige dieser Nachrichten. Zur Erinnerung: Angebote sind Snippets von Code/Inhalt, die in der Antwort [!DNL Target] bereitgestellt werden. Sie werden meist in der [!DNL Target]-Benutzeroberfläche erstellt, können aber auch über API oder die Experience Fragments-Integration mit Adobe Experience Manager erstellt werden. In mobilen Apps sind JSON-Angebote häufig. In diesem Tutorial verwenden wir HTML-Angebote, mit denen Sie beliebige Textinhalte (einschließlich JSON) in der App bereitstellen können.

### Erstellen von Angeboten für neue Benutzer

Erstellen wir zunächst Angebote für die Nachrichten an neue Benutzer:

1. Klicken Sie in der oberen Navigation auf **[!UICONTROL Angebote]** .
1. Klicken Sie auf **[!UICONTROL Erstellen]**.
1. Wählen Sie **[!UICONTROL HTML Offer]** aus.

   ![Erstellen eines Startangebots](assets/offer_home_1.jpg)

1. Benennen Sie das Angebot _Startseite: Neue Benutzer einbinden_.
1. Geben Sie _Quelle und Ziel auswählen, um nach verfügbaren Bussen_ als Code zu suchen.
1. Speichern Sie das neue Angebot.

   ![Erstellen von Home-HTML-Angeboten](assets/offer_home_2.jpg)

### Erstellen des Angebots für wiederkehrende Benutzer

Erstellen wir nun das erste Angebot für wiederkehrende Benutzer (das zweite Angebot wird Standardinhalt sein, der als nichts angezeigt wird):

1. Benennen Sie das Angebot _Startseite: Zurückgeben von Benutzern_.
1. Geben Sie _Willkommen zurück! Verwenden Sie den Promo-Code BACK30 während des Checkouts, um einen 10-%-Rabatt zu erhalten._ als HTML-Code.
1. Speichern Sie das neue Angebot.

   ![Erstellen von Home-HTML-Angeboten](assets/offer_home_returning_users.jpg)

### San Diego-Angebot erstellen

Wenn &quot;DJ&quot;an die Aktivität &quot;Vielen Dank!&quot;zurückgegeben wird, zeigt die Logik in der Funktion filterRecommendationBasedOnOffer() ein Banner für &quot;Rock Night with DJ SAM&quot;an:

1. Benennen Sie das Angebot _Promotion für San Diego_.
1. Geben Sie _DJ_ als HTML-Code ein.
1. Speichern Sie das neue Angebot.

![Erstellen von &quot;San Diego&quot;-Angeboten](assets/offer_san_diego.jpg)

### Erstellen eines Angebots für Benutzer, die nach Los Angeles gehen

Wenn &quot;Universal&quot;zur Aktivität &quot;Vielen Dank!&quot;zurückgegeben wird, zeigt die Logik in der Funktion filterRecommendationBasedOnOffer() ein Banner für &quot;Universal Studios&quot;an:

1. Benennen Sie das Angebot _Promotion für Los Angeles_.
1. Geben Sie _Universal_ als HTML-Code ein.
1. Speichern Sie das neue Angebot.

![&quot;Los Angeles&quot;-Angebot erstellen](assets/offer_los_angeles.jpg)

## Schlussfolgerung 

Jetzt haben wir unsere Zielgruppen und Angebote. In der nächsten Lektion erstellen wir Aktivitäten, die die Orte, Zielgruppen und Angebote miteinander verknüpfen, um personalisierte Erlebnisse zu erstellen!

**[NÄCHSTES : &quot;Layouts personalisieren&quot;>](personalize-layouts.md)**
