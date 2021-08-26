---
title: Parameter zu Anforderungen hinzufügen
description: In dieser Lektion fügen wir den in der vorherigen Lektion hinzugefügten Target-Anforderungen Lebenszyklusmetriken und benutzerdefinierte Adoben hinzu. Diese Metriken und Parameter werden später im Tutorial zum Erstellen personalisierter Zielgruppen verwendet.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
thumbnail: null
exl-id: 0250e55f-a233-4060-84e1-86d1f88a6106
source-git-commit: a6b645b6d9693a4c8882fd47ee0d61698c0b834d
workflow-type: tm+mt
source-wordcount: '829'
ht-degree: 0%

---

# Parameter zu Anforderungen hinzufügen

In dieser Lektion fügen wir den in der vorherigen Lektion hinzugefügten [!DNL Target] -Anforderungen Adobe-Lebenszyklusmetriken und benutzerdefinierte Parameter hinzu. Diese Metriken und Parameter werden später im Tutorial zum Erstellen personalisierter Zielgruppen verwendet.

## Lernziele

Am Ende dieser Lektion können Sie:

* Mobile Lebenszyklusmetriken der Adobe hinzufügen
* Parameter zu einer Vorabruf-Anfrage hinzufügen
* Parameter zu einem Live-Speicherort hinzufügen
* Überprüfen der Parameter für beide Anforderungen

## Hinzufügen der Lebenszyklusparameter

Lassen Sie uns die Metriken [Mobile Lebenszyklusmetriken der Adobe](https://docs.adobe.com/content/help/en/mobile-services/android/metrics.html) aktivieren. Dadurch werden Parameter zu Standortanfragen hinzugefügt, die umfassende Informationen über das Gerät des Benutzers und die Interaktion mit der App enthalten. Wir erstellen Zielgruppen in der nächsten Lektion anhand von Daten, die die Lebenszyklusanfrage bereitstellt.

Um Lebenszyklusmetriken zu aktivieren, öffnen Sie den HomeActivity-Controller erneut und fügen Sie `Config.collectLifecycleData(this);` zur Funktion onResume() hinzu:

![Lebenszyklusanforderung](assets/lifecycle_code.jpg)

### Validieren der Lebenszyklusparameter für die Vorabruf-Anfrage

Führen Sie den Emulator aus und überprüfen Sie mithilfe von Logcat die Lebenszyklusparameter. Filtern Sie nach &quot;prefetch&quot;, um die Vorabruf-Antwort zu finden und nach den neuen Parametern zu suchen:
![Lebenszyklusvalidierung](assets/lifecycle_validation.jpg)

Auch wenn wir dem HomeActivity-Controller nur `Config.collectLifecycleData()` hinzugefügt haben, sollten Sie die Lebenszyklusmetriken sehen, die mit der Target-Anfrage auch auf Ihrem Dankeschön-Bildschirm gesendet wurden.

## Fügen Sie den Parameter at_property zur Vorababruf-Anfrage hinzu.

Adobe Target-Eigenschaften werden in der [!DNL Target]-Benutzeroberfläche definiert und dienen zur Festlegung von Grenzen für die Personalisierung von Apps und Websites. Der Parameter at_property gibt die spezifische Eigenschaft an, in der auf Ihre Angebote und Aktivitäten zugegriffen und diese verwaltet werden. Wir fügen eine Eigenschaft zu den Anfragen für den Vorabruf und den Live-Speicherort hinzu.

>[!NOTE]
>
>Abhängig von Ihrer Lizenz werden Ihnen in der [!DNL Target] -Benutzeroberfläche möglicherweise die Eigenschaften -Optionen angezeigt. Wenn Sie diese Optionen nicht haben oder Eigenschaften nicht in Ihrem Unternehmen verwenden, fahren Sie einfach mit dem nächsten Abschnitt dieser Lektion fort.

Sie können Ihren at_property-Wert in der [!DNL Target]-Benutzeroberfläche unter [!UICONTROL Setup] > [!UICONTROL Eigenschaften] abrufen.  Bewegen Sie den Mauszeiger über die Eigenschaft, wählen Sie das Symbol für das Codefragment aus und kopieren Sie den Wert `at_property` :

![&quot;at_property&quot;kopieren](assets/at_property_interface.jpg)

Fügen Sie ihn als Parameter für jeden Speicherort in der Vorabruf-Anfrage wie folgt hinzu:
![Fügen Sie at_property parameter](assets/params_at_property.jpg) hinzu
Hier finden Sie den aktualisierten Code für die Funktion `targetPrefetchContent()` (aktualisieren Sie den _[!UICONTROL Ihr at_property -Wert hier]_ Platzhaltertext!):

```java
public void targetPrefetchContent() {
        List<TargetPrefetchObject> prefetchList = new ArrayList<>();

        Map<String, Object> params1;
        params1 = new HashMap<String, Object>();
        params1.put("at_property", "your at_property value goes here");

        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, params1));
        prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, params1));
        Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
            @Override
            public void call(final Boolean status) {
                HomeActivity.this.runOnUiThread(new Runnable() {
                    @Override
                    public void run() {
                        String cachingStatus = status ? "YES" : "NO";
                        System.out.println("Received Response from prefetch : " + cachingStatus);
                        engageMessage();
                        setUp();

                    }
                });
            }};
        Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
    }
```

### Hinweis zu Parametern

Für zukünftige Projekte können Sie zusätzliche Parameter implementieren. Die `createTargetPrefetchObject()`-Methode ermöglicht drei Parametertypen: `locationParams`, `orderParams` und `productParams`. Weitere Informationen zum Hinzufügen dieser Parameter zur Vorabruf-Anfrage](https://experienceleague.adobe.com/docs/mobile-services/android/target-android/c-mob-target-prefetch-android.html?lang=en) finden Sie in der Dokumentation zu [.

Beachten Sie außerdem, dass jedem Speicherort in der Vorabruf-Anfrage verschiedene Positionsparameter hinzugefügt werden können. Sie können beispielsweise eine weitere Map mit dem Namen param2 erstellen, einen neuen Parameter darin einfügen und dann param2 an einer Position und param1 an der anderen Position festlegen. Im Folgenden finden Sie ein Beispiel:

```java
prefetchList.add(Target.createTargetPrefetchObject(location1_name, params1);
prefetchList.add(Target.createTargetPrefetchObject(location2_name, params2);
```

## Überprüfen des Parameters at_property in der Vorabruf-Anfrage

Führen Sie nun den Emulator aus und überprüfen Sie mit Logcat, ob die at_property in der Vorabruf-Anfrage und -Antwort für beide Speicherorte angezeigt wird:
![Validieren Sie den Parameter at_property](assets/parameters_at_property_validation.jpg)

## Hinzufügen benutzerdefinierter Parameter zur Anforderung des Live-Standorts

Die Live-Ortsanforderung (wetravel_context_dest) wurde in der vorherigen Lektion hinzugefügt, sodass wir eine relevante Promotion auf dem letzten Bestätigungsbildschirm des Buchungsprozesses anzeigen konnten. Wir möchten die Promotion basierend auf dem Ziel des Benutzers personalisieren und fügen dies als Parameter zur Anfrage hinzu. Wir fügen auch einen Parameter für den Ursprung der Gruppe und den Wert at_property hinzu.

Fügen Sie die folgenden Parameter zur Funktion targetLoadRequest() im Controller &quot;Vielen DankYouActivity&quot;hinzu:
![Parameter zur Anforderung des Live-Standorts hinzufügen](assets/parameters_live_location.jpg)
Hier finden Sie den aktualisierten Code für die Funktion targetLoadRequest() (aktualisieren Sie den Platzhaltertext &quot;at_property value here&quot;):

```java
public void targetLoadRequest(final ArrayList<Recommandation> recommandations) {
    Map<String, Object> locationParams = new HashMap<>();
    locationParams.put("at_property","add your at_property value here");
    locationParams.put("locationSrc", (""+Utility.getInSharedPreference(ThankYouActivity.this,Constant.departure,"")));
    locationParams.put("locationDest", (""+Utility.getInSharedPreference(ThankYouActivity.this,Constant.destination,"")));

    Target.loadRequest(Constant.wetravel_context_dest, "", null, null, locationParams, new Target.TargetCallback<String>() {
        @Override
        public void call(final String response) {
        try {
            runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    AppDialogs.dialogLoaderHide();
                    filterRecommendationBasedOnOffer(recommandations, response);
                    recommandationbAdapter.notifyDataSetChanged();
                }
            });
        } catch (Exception e) {
            e.printStackTrace();
        }
        }
    });
    Target.clearPrefetchCache();
}
```

### Überprüfen der benutzerdefinierten Parameter in der Anforderung &quot;Live-Position&quot;

Führen Sie den Emulator aus und öffnen Sie Logcat. Filtern Sie nach einem der Parameter, um zu überprüfen, ob die Anforderung die erforderlichen Parameter enthält:
![Überprüfen Sie die benutzerdefinierten Parameter in der Anforderung für die Live-Position](assets/parameters_live_location_validation.jpg)

>[!NOTE]
>
>Bestellbestätigungsanfragen und -parameter: Obwohl in diesem Demoprojekt nicht verwendet, werden Bestelldetails in der Regel in einer echten Implementierung erfasst, sodass [!DNL Target] Bestelldetails als Metriken/Dimensionen verwenden kann. Anweisungen zum Implementieren der Bestellbestätigungsanforderung und der Parameter](https://experienceleague.adobe.com/docs/mobile-services/android/target-android/c-target-methods.html?lang=en) finden Sie in der Dokumentation .[

>[!NOTE]
>
>Analytics for Target (A4T): Adobe Analytics kann als Berichtsquelle für [!DNL Target] konfiguriert werden. Dadurch können alle vom Target SDK erfassten Metriken/Dimensionen in Adobe Analytics angezeigt werden. Weitere Informationen finden Sie unter [A4T-Übersicht](https://experienceleague.adobe.com/docs/target/using/integrate/a4t/a4t.html?lang=en) .

Gute Arbeit! Nachdem die Parameter eingerichtet sind, können wir diese Parameter verwenden, um Zielgruppen und Angebote in Adobe Target zu erstellen.

**[NÄCHSTES : &quot;Erstellen von Zielgruppen und Angeboten&quot;>](create-audiences-and-offers.md)**
