---
title: hinzufügen von Parametern für Anforderungen
description: In dieser Lektion werden den in der vorherigen Lektion hinzugefügten Zielgruppen Lebenszyklusmetriken und benutzerdefinierte Adoben hinzugefügt. Diese Metriken und Parameter werden später im Tutorial zur Erstellung personalisierter Audiencen verwendet.
role: Entwickler
level: Zwischenschaltung
topic: Mobil, Personalisierung
feature: Mobile implementieren
doc-type: tutorial
kt: 3040
thumbnail: null
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 0%

---


# hinzufügen von Parametern für Anforderungen

In dieser Lektion werden den in der vorherigen Lektion hinzugefügten [!DNL Target]-Anforderungen Lebenszyklusmetriken und benutzerdefinierte Adoben hinzugefügt. Diese Metriken und Parameter werden später im Tutorial zur Erstellung personalisierter Audiencen verwendet.

## Lernziele

Am Ende dieser Lektion können Sie:

* hinzufügen der Lebenszyklusmetriken der Adobe
* hinzufügen von Parametern für eine Anforderung zum vorherigen Abrufen
* hinzufügen von Parametern an einen Live-Speicherort
* Validieren der Parameter für beide Anforderungen

## hinzufügen der Lebenszyklusparameter

Aktivieren wir die Metriken [Mobil-Lebenszyklusmetriken der Adobe](https://docs.adobe.com/content/help/en/mobile-services/android/metrics.html). Auf diese Weise werden Ortsanforderungen Parameter hinzugefügt, die ausführliche Informationen über das Gerät des Benutzers und die Interaktion mit der App enthalten. In der nächsten Lektion erstellen wir Audiencen anhand von Daten, die die Lebenszyklusanforderung bereitstellt.

Um Lebenszyklusmetriken zu aktivieren, öffnen Sie den HomeActivity-Controller erneut und fügen Sie der Funktion onResume() `Config.collectLifecycleData(this);` hinzu:

![Lebenszyklusanforderung](assets/lifecycle_code.jpg)

### Überprüfen der Lebenszyklusparameter für die Abfrage vor dem Abrufen

Führen Sie den Emulator aus und verwenden Sie Logcat, um die Lebenszyklusparameter zu validieren. Filtern Sie nach &quot;prefetch&quot;, um die Antwort vor dem Abrufen zu finden und nach den neuen Parametern zu suchen:
![Lebenszyklusvalidierung](assets/lifecycle_validation.jpg)

Auch wenn wir dem HomeActivity-Controller nur `Config.collectLifecycleData()` hinzugefügt haben, sollten Sie auch die Lebenszyklusmetriken sehen, die mit der Anforderung zur Zielgruppe gesendet wurden, die auf Ihrem Dankesbildschirm angezeigt werden.

## hinzufügen des Parameters &quot;at_property&quot;zur Anforderung &quot;Prefetch&quot;

Adobe Target-Eigenschaften werden in der [!DNL Target]-Schnittstelle definiert und dienen zur Festlegung von Grenzen für die Personalisierung von Apps und Websites. Der Parameter at_property gibt die spezifische Eigenschaft an, in der auf Ihre Angebot und Aktivitäten zugegriffen und diese gepflegt werden. Wir fügen eine Eigenschaft zu den Anforderungen für den vorherigen und den Live-Standort hinzu.

>[!NOTE]
>
>Abhängig von Ihrer Lizenz sehen Sie möglicherweise die Optionen Eigenschaften in der [!DNL Target]-Schnittstelle. Wenn Sie diese Optionen nicht haben oder Eigenschaften nicht in Ihrer Firma verwenden, fahren Sie einfach mit dem nächsten Abschnitt dieser Lektion fort.

Sie können den Wert at_property in der [!DNL Target]-Schnittstelle unter [!UICONTROL Setup] > [!UICONTROL Eigenschaften] abrufen.  Bewegen Sie den Mauszeiger über die Eigenschaft, wählen Sie das Symbol für das Codefragment und kopieren Sie den Wert `at_property`:

![Kopieren Sie at_property](assets/at_property_interface.jpg)

hinzufügen es als Parameter für jeden Speicherort in der Abfrage vor dem Abrufen wie folgt:
![Hinzufügen at_property-Parameter](assets/params_at_property.jpg)
Im Folgenden finden Sie den aktualisierten Code für die Funktion `targetPrefetchContent()` (aktualisieren Sie den Wert _[!UICONTROL Ihre at_property hier]_ Platzhaltertext!):

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

Für zukünftige Projekte sollten Sie zusätzliche Parameter implementieren. Die `createTargetPrefetchObject()`-Methode erlaubt drei Parametertypen: `locationParams`, `orderParams` und `productParams`. Weitere Informationen zum Hinzufügen dieser Parameter zur Abfrage vor dem Abrufen finden Sie in der Dokumentation für [.](https://docs.adobe.com/content/help/en/mobile-services/android/target-android/c-mob-target-prefetch-android.html)

Beachten Sie außerdem, dass jeder Position in der Abfrage vor dem Abrufen verschiedene Positionsparameter hinzugefügt werden können. Sie können beispielsweise eine weitere Map mit dem Namen param2 erstellen, einen neuen Parameter darin einfügen und dann param2 an einem Ort und param1 an dem anderen Ort festlegen. Hier ein Beispiel:

```java
prefetchList.add(Target.createTargetPrefetchObject(location1_name, params1);
prefetchList.add(Target.createTargetPrefetchObject(location2_name, params2);
```

## Validieren des Parameters at_property in der Prefetch-Anforderung

Führen Sie nun den Emulator aus und überprüfen Sie mithilfe von Logcat, ob die at_property bei der Anfrage und Antwort vor dem Abrufen für beide Speicherorte angezeigt wird:
![Validieren Sie den at_property-Parameter](assets/parameters_at_property_validation.jpg)

## hinzufügen benutzerdefinierter Parameter zur Anforderung des Live-Speicherorts

Die Live-Ortsanforderung (wetravel_context_dest) wurde in der vorherigen Lektion hinzugefügt, sodass wir eine entsprechende Promotion auf dem letzten Bestätigungsbildschirm des Buchungsprozesses anzeigen konnten. Wir möchten die Promotion auf Basis des Zielorts des Benutzers personalisieren und dies als Parameter zur Anforderung hinzufügen. Wir fügen einen Parameter für die Herkunft &quot;trop&quot;und den Wert &quot;at_property&quot;hinzu.

hinzufügen Sie die folgenden Parameter an die Funktion targetLoadRequest() im DankeschönActivity-Controller:
![Hinzufügen Parameter für die Anforderung des Live-Standorts](assets/parameters_live_location.jpg)
Im Folgenden finden Sie den aktualisierten Code für die Funktion targetLoadRequest() (aktualisieren Sie den Platzhaltertext &quot;Fügen Sie hier Ihren at_property-Wert hinzu&quot;):

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

### Validieren der benutzerdefinierten Parameter in der Anforderung &quot;Live-Position&quot;

Führen Sie den Emulator aus und öffnen Sie Logcat. Filtern Sie nach einem der Parameter, um sicherzustellen, dass die Anforderung die erforderlichen Parameter enthält:
![Validieren Sie die benutzerdefinierten Parameter in der Anforderung für den Live-Standort](assets/parameters_live_location_validation.jpg)

>[!NOTE]
>
>Bestellbestätigungsanfragen und -parameter: Obwohl in diesem Demo-Projekt nicht verwendet, werden Bestelldetails in der Regel in einer echten Implementierung erfasst, sodass [!DNL Target] Bestelldetails als Metriken/Dimensionen verwenden kann. Anweisungen zur Implementierung der Bestellbestätigungsanforderung und der Parameter [finden Sie in der Dokumentation.](https://docs.adobe.com/content/help/en/mobile-services/android/target-android/c-target-methods.html)

>[!NOTE]
>
>Analytics for Zielgruppe (A4T): Adobe Analytics kann als Berichte-Quelle für [!DNL Target] konfiguriert werden. Dadurch können alle vom Zielgruppe SDK erfassten Metriken/Dimensionen in Adobe Analytics angezeigt werden. Weitere Informationen finden Sie unter [A4T-Übersicht](https://docs.adobe.com/content/help/en/target/using/integrate/a4t/a4t.html).

Gute Arbeit! Jetzt, da Parameter vorhanden sind, können wir diese Parameter verwenden, um Audiencen und Angebot in Adobe Target zu erstellen.

**[NÄCHSTES: &quot;Audiencen und Angebot erstellen&quot;>](create-audiences-and-offers.md)**
