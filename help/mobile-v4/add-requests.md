---
title: Hinzufügen von Adobe Target-Anforderungen
description: Das Adobe Mobile Services SDK (v4) bietet Adobe Target-Methoden und -Funktionen, mit denen Sie Ihre App mit unterschiedlichen Benutzererlebnissen personalisieren können.
role: Developer
level: Intermediate
topic: Mobile, Personalization
feature: Implement Mobile
doc-type: tutorial
kt: 3040
exl-id: 88a5be3f-d61f-43e7-997a-574ef56122ed
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '1785'
ht-degree: 0%

---

# Hinzufügen von Adobe Target-Anforderungen

Das Adobe Mobile Services SDK (v4) bietet Adobe Target-Methoden und -Funktionen, mit denen Sie Ihre App mit unterschiedlichen Benutzererlebnissen personalisieren können. In der Regel werden eine oder mehrere Anfragen von der App an die Adobe Target gesendet, um den personalisierten Inhalt abzurufen und die Wirkung dieses Inhalts zu messen.

In dieser Lektion bereiten Sie die We.Travel-App für die Personalisierung vor, indem Sie [!DNL Target] -Anforderungen implementieren.

## Voraussetzungen 

Stellen Sie sicher, dass Sie [die Beispielanwendung herunterladen und aktualisieren](download-and-update-the-sample-app.md).

## Lernziele

Am Ende dieser Lektion können Sie:

* Zwischenspeichern mehrerer [!DNL Target] Angebote (d. h. personalisierter Inhalt) mithilfe einer Batch-Vorabruf-Anfrage
* Vorab abgerufene [!DNL Target] Speicherorte laden
* Laden eines [!DNL Target] -Speicherorts in Echtzeit (nicht vorab abgerufen)
* Vorab abgerufene Speicherorte aus dem Cache löschen
* Vorabgerufene und Echtzeitanforderungen validieren

## Terminologie  

Nachstehend finden Sie einige der wichtigsten Target-Terminologie, die wir im Rest dieses Tutorials verwenden werden.

* **Anfrage:** eine Netzwerkanforderung an die Adobe Target-Server
* **Angebot:** ein Codeausschnitt oder anderen textbasierten Inhalt, der in der [!DNL Target] -Benutzeroberfläche (oder mit API) definiert ist und in der Antwort bereitgestellt wird. Normalerweise JSON, wenn [!DNL Target] in nativen mobilen Apps verwendet wird.
* **Ort:** ein benutzerdefinierter Name, der einer Anfrage gegeben wird und in der [!DNL Target] -Oberfläche zum Verknüpfen von Angeboten mit bestimmten Anforderungen verwendet wird
* **Batch-Anfrage:** eine einzelne Anfrage mit mehreren Speicherorten
* **Vorabruf-Anfrage:** eine einzelne Anfrage, die Angebote abruft und in den Speicher zwischenspeichert, um sie für die zukünftige Verwendung in der App nutzen zu können
* **Batch-Vorabruf-Anfrage:** eine einzelne Anfrage, die Angebote für mehrere Orte vorab abruft
* **Zielgruppe:** eine Besuchergruppe, die in der [!DNL Target] -Benutzeroberfläche definiert oder von anderen Adobe-Applikationen (z. B. &quot;iPhone X-Besucher&quot;, &quot;Besucher in Kalifornien&quot;, &quot;Erste App-Öffnung&quot;) für [!DNL Target] freigegeben wurde.
* **Aktivität:** ein [!DNL Target] -Konstrukt, das in der [!DNL Target] -Benutzeroberfläche (oder mit API) definiert ist und Positionen, Angebote und Zielgruppen verknüpft, um ein personalisiertes Erlebnis zu erstellen

## Hinzufügen einer Batch-Vorabruf-Anfrage

Die erste Anfrage, die wir in We.Travel implementieren werden, ist eine Batch-Vorabruf-Anfrage mit zwei [!DNL Target] -Stellen auf dem Startbildschirm. In einer späteren Lektion konfigurieren wir Angebote für diese Orte, die Nachrichten anzeigen, um neue Benutzer durch den Buchungsprozess zu führen.

Eine Vorabruf-Anfrage ruft so wenig wie möglich [!DNL Target] -Inhalte ab, indem die Adobe Target-Serverantwort (Angebot) zwischengespeichert wird. Eine Batch-Vorabruf-Anfrage ruft mehrere Angebote ab und speichert sie zwischen, die jeweils einem anderen Ort zugeordnet sind. Alle vorab abgerufenen Speicherorte werden auf dem Gerät zwischengespeichert und können künftig in der Benutzersitzung verwendet werden. Durch den Vorabruf mehrerer Orte auf dem Startbildschirm können wir Angebote abrufen, die später verwendet werden, wenn der Besucher durch die App navigiert. Weitere Informationen zu den Vorabrufmethoden finden Sie in der [Dokumentation zum Vorabruf](https://experienceleague.adobe.com/docs/mobile-services/android/target-android/c-mob-target-prefetch-android.html?lang=en) .

### Hinzufügen der Batch-Vorabruf-Anfrage

Aktualisieren wir nun den HomeActivity-Controller (den Quellcode des Home-Bildschirms), der sich unter &quot;app > main > java > com.wetravel > Controller&quot;befindet. Wir fügen die beiden Codeblöcke in rot hinzu:

Beginnen wir mit dem HomeActivity-Controller (dem Quellcode des Home-Bildschirms), der sich unter &quot;app > main > java > com.webvel > Controller&quot;befindet.

Wir fügen die beiden Codeblöcke in rot hinzu:

![HomeActivity-Vorabruf-Code](assets/homeactivity.jpg)

Scrollen Sie nach unten zum Ende des Codes von HomeActivity und fügen Sie den unten angegebenen Code nach der Funktion `setHeader()` und *Ersetzen* der aktuellen Funktion `onResume()` hinzu:

```java
@Override
protected void onResume() {
    super.onResume();
    targetPrefetchContent();
}

public void targetPrefetchContent() {
    List<TargetPrefetchObject> prefetchList = new ArrayList<>();
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_home, null));
    prefetchList.add(Target.createTargetPrefetchObject(Constant.wetravel_engage_search, null));
    Target.TargetCallback<Boolean> prefetchStatusCallback = new Target.TargetCallback<Boolean>() {
        @Override
        public void call(final Boolean status) {
            HomeActivity.this.runOnUiThread(new Runnable() {
                @Override
                public void run() {
                    String cachingStatus = status ? "YES" : "NO";
                    System.out.println("Received Response from prefetch : " + cachingStatus);
                    setUp();

                }
            });
        }};
    Target.prefetchContent(prefetchList, null, prefetchStatusCallback);
}
```

Ihre IDE wird Sie wahrscheinlich darauf hinweisen, dass die [!DNL Target]-Klassen nicht in die Datei importiert wurden. Importieren Sie unbedingt die [!DNL Target]-Klassen oben im HomeActivity-Controller, wie unten in Rot dargestellt:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

![Importieren der Zielklassen](assets/import.jpg)

Sie werden wahrscheinlich auch Fehler für &quot;kann die Symbolvariable wetravel_engage_home nicht finden&quot;und &quot;Symbolvariable wetravel_engage_search kann nicht gefunden werden&quot;sehen. Fügen Sie diese zur Datei `Constant.java` hinzu (in App > src > main > java > com > wetravel > Utils):

```java
public static final String wetravel_engage_home = "wetravel_engage_home";
public static final String wetravel_engage_search = "wetravel_engage_search";
```

![Fügen Sie der Datei &quot;Constant.java&quot;die Ortsnamen hinzu](assets/constants.jpg)

### Erläuterung des Anforderungscodes für den Batch-Vorabruf

| Code | Beschreibung |
|--- |--- |
| `targetPrefetchContent()` | Eine benutzerdefinierte Funktion (nicht Teil des SDK), die mithilfe von [!DNL Target] -Methoden zwei [!DNL Target]-Speicherorte abruft und zwischenspeichert. |
| `prefetchContent()` | Die [!DNL Target] SDK-Methode, die die Vorabruf-Anfrage sendet |
| `Constant.wetravel_engage_home` | Vorab abgerufener [!DNL Target] Ortsname, der den Angebotsinhalt auf dem Startbildschirm anzeigt |
| `Constant.wetravel_engage_search` | Vorab abgerufener [!DNL Target] Ortsname, der den Angebotsinhalt auf dem Suchergebnisbildschirm anzeigt. Da dies ein zweiter Speicherort im Vorabruf ist, wird diese Vorabruf-Anfrage als &quot;Vorabruf-Batch-Anfrage&quot;bezeichnet. |
| setUp() | Eine benutzerdefinierte Funktion, die den Startbildschirm der App rendert, nachdem die [!DNL Target] -Angebote vorabgerufen wurden |

### Über asynchrone und synchrone

Mit dem soeben implementierten Code wird die Vorabruf-Anfrage als synchroner, blockierender Aufruf ausgeführt, kurz bevor der Startbildschirm gerendert wird. Als wir den neuen Code in den HomeActivity-Controller eingefügt haben, haben wir die Ausführung der `setUp()` -Funktion von der `onResume()` -Funktion bis nach der Target-Anfrage verschoben. Dies kann in Szenarien nützlich sein, in denen Sie Inhalte personalisieren möchten, wenn die App zum ersten Mal geöffnet wird, da dadurch sichergestellt wird, dass personalisierte Inhalte von den Target-Servern vor dem ersten Rendering des Bildschirms zurückgegeben (oder abgelaufen) werden. Damit die Anforderungen asynchron geladen werden können (im Hintergrund), rufen Sie stattdessen `setUp()` innerhalb der Funktion `onCreate()` auf.

### Validieren der Batch-Vorabruf-Anfrage

Erstellen Sie die App neu und öffnen Sie den Android-Emulator. (Die folgenden Screenshots verwenden Pixel 2 auf Android Q Version 9+, API-Ebene 29). Die Vorabruf-Antwort sollte &quot;Vorabruf-Antwort erhalten&quot;lauten:

Wenn der Startbildschirm gerendert wird, sollte die Vorabruf-Anfrage geladen werden. Filtern Sie mit Logcat nach [!DNL "Target"], um die Anfrage und Antwort anzuzeigen:

![Überprüfen der Anforderungen auf dem Startbildschirm](assets/prefetch_validation.jpg)

Wenn keine erfolgreiche Antwort angezeigt wird, überprüfen Sie die Einstellungen in der Datei `ADBMobileConfig.json` und die Codesyntax in der Datei HomeActivity .

Zwei Speicherorte werden jetzt auf dem Gerät zwischengespeichert. Die Ortsnamen werden in Kürze verzögert in die Oberfläche [!DNL Target] geladen, wo sie in verschiedenen Dropdown-Menüs ausgewählt werden können, wenn Sie sie in einer Aktivität verwenden.

### Hinzufügen von Ladeanforderungen für jeden zwischengespeicherten Speicherort

Nachdem die Speicherorte vorabgerufen und ihre Antworten auf dem Gerät zwischengespeichert wurden, fügen wir die Methode `Target.loadRequest()` hinzu, mit der der Angebotsinhalt aus dem Cache abgerufen wird, damit Sie damit Ihre Anwendung aktualisieren können. Wir fügen eine neue benutzerdefinierte Methode mit dem Namen `engageMessage()` hinzu, die mit der Vorabruf-Anfrage ausgeführt wird. `engageMessage()` ruft `Target.loadRequest()` auf. `engageMessage()` wird vor `setUp()` ausgeführt, um sicherzustellen, dass die Ladeanforderung aufgerufen wird, bevor der Bildschirm eingerichtet wird.

Fügen Sie zunächst den `engageMessage()` -Aufruf und die -Methode für den Standort &quot;wetravel_engage_home&quot;in der HomeActivity hinzu:

![Erste Ladeanforderung hinzufügen](assets/wetravel_engage_home_loadRequest.jpg)

Hier finden Sie den aktualisierten Code:

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
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_home, "", null, null, null,
            new Target.TargetCallback<String>(){
                @Override
                public void call(final String s) {
                    runOnUiThread(new Runnable() {
                        @Override
                        public void run() {
                            System.out.println("Engage Message : " + s);
                            if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                        }
                    });
                }
            });
    }
```

Fügen Sie nun den `engageMessage()` -Aufruf und die Methode für die Position &quot;wetravel_engage_search&quot;in SearchBusActivity hinzu. Beachten Sie, dass der `engageMessage()` -Aufruf in der `onResume()` -Methode vor dem Aufruf von `setUpSearch()` festgelegt ist, sodass er ausgeführt wird, bevor der Bildschirm eingerichtet wird:

![Zweite Ladeanforderung hinzufügen](assets/wetravel_engage_search_loadRequest.jpg)

Hier finden Sie den aktualisierten Code:

```java
    @Override
    public void onResume() {
        super.onResume();
        engageMessage();
        setUpSearch();
    }
    public void engageMessage() {
        Target.loadRequest(Constant.wetravel_engage_search, "", null, null, null,
                new Target.TargetCallback<String>(){
                    @Override
                    public void call(final String s) {
                        runOnUiThread(new Runnable() {
                            @Override
                            public void run() {
                                System.out.println("Engage Message : " + s);
                                if(s != null && !s.isEmpty()) Utility.showToast(getApplicationContext(), s);
                            }
                        });
                    }
                });
    }
```

Da Sie gerade Target-Methoden zur SearchBusActivity hinzugefügt haben, müssen Sie die [!DNL Target]-Klassen importieren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

## Hinzufügen einer Echtzeitanforderung

Die nächste Anfrage, die wir der App hinzufügen werden, ist eine Echtzeitanforderung auf dem Bildschirm &quot;Vielen Dank&quot;. Mit &quot;Echtzeit&quot;meinen wir, dass sowohl die Anfrage als auch die Antwort sofort angewendet wird (nicht für später zwischengespeichert). In einer späteren Lektion erstellen wir mithilfe dieser Anfrage ein Erlebnis, das für das Reiseziel des Benutzers personalisiert ist.

Fügen wir also eine Echtzeitanforderung auf dem Dankesbildschirm hinzu. In der Datei &quot;Vielen DankYouActivity&quot;nehmen wir die in Rot angezeigten Änderungen vor:
![Fügen Sie auf dem Dankesbildschirm einen Echtzeitstandort hinzu](assets/thankyou.jpg)

Scrollen Sie zum Ende der Datei &quot;Vielen Dank! Kommentieren Sie die drei Zeilen in der Funktion `getRecommandations()` aus und fügen Sie den Aufruf der Funktion `targetLoadRequest()` hinzu:

```java
// AppDialogs.dialogLoaderHide();
// recommandations.addAll(recommandation.recommandations);
// recommandationbAdapter.notifyDataSetChanged();
```

Fügen Sie diese Codezeile zur Funktion `getRecommandations()` hinzu:

```java
targetLoadRequest(recommandation.recommandations);
```

Jetzt müssen wir die Funktion `targetLoadRequest()` definieren:
![Fügen Sie auf dem Dankesbildschirm einen Echtzeitstandort hinzu](assets/thankyou2.jpg)

Fügen Sie diesen Codeblock nach der Funktion `filterRecommendationBasedOnOffer()` hinzu:

```java
public void targetLoadRequest(final ArrayList<Recommandation> recommandations) {
    Target.loadRequest(Constant.wetravel_context_dest, "", null, null, null, new Target.TargetCallback<String>() {
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
}
```

Da Sie soeben Target-Methoden zur Dankesaktivität hinzugefügt haben, müssen Sie die Target-Klassen importieren:

```java
import com.adobe.mobile.Target;
import com.adobe.mobile.TargetPrefetchObject;
```

### targetLoadRequest()-Codeerläuterung

| Code | Beschreibung |
|--- |--- |
| `targetLoadRequest()` | Eine benutzerdefinierte Funktion (nicht Teil des SDK), die `Target.loadRequest()` auslöst, die den Standort &quot;wetravel_context_dest&quot;lädt und anzeigt |
| `Target.loadRequest()` | Die SDK-Methode, die die Anfrage an den Target-Server sendet |
| Constant.wetravel_context_dest | Der der Anfrage zugewiesene Ortsname, den wir später verwenden, wenn wir die Aktivität in der [!DNL Target] -Oberfläche erstellen |
| `filterRecommendationBasedOnOffer()` | Eine benutzerdefinierte Funktion in der App, die das Angebot der Position aus der Target-Antwort übernimmt und entscheidet, wie die App basierend auf dem Inhalt des Angebots geändert werden soll |
| `recommandations.addAll()` | Eine benutzerdefinierte Funktion in der App, die standardmäßig ausgeführt wurde, wenn der Bildschirm Vielen Dank geladen wurde, jetzt jedoch ausgeführt wird, nachdem die Target-Antwort empfangen und von `filterRecommendationBasedOnOffer()` geparst wurde |

Dies war eine komplexere Aktualisierung, die wir dann mit der Anfrage, die wir zum Startbildschirm hinzugefügt haben, an die App vorgenommen haben. Schauen wir uns also kurz an, was wir getan haben:

1. Das vorherige Verhalten der App bei der Anzeige von drei Standardaktionen wurde unterbrochen, indem die Codezeilen auskommentiert wurden.
1. Wir haben der App stattdessen empfohlen, eine neue Funktion auszuführen, die wir willkürlich targetLoadRequest nennen
1. Wir haben die Funktion `targetLoadRequest` definiert, um mithilfe der Methode Target.loadRequest eine Anfrage an Target zu senden und sofort die Funktion `filterRecommendationBasedOnOffer()` auszuführen, wenn die Angebotsantwort [!DNL Target] empfangen wird.
1. Die Funktion `filterRecommendationBasedOnOffer()` interpretiert die Antwort und entscheidet, welche Promotions auf den Bildschirm angewendet werden sollen

Dies ist ein sehr häufiges Nutzungsmuster bei der Verwendung von [!DNL Target] in Apps.  Es ist sehr leistungsstark, da Sie fast jeden Aspekt Ihrer App personalisieren können. Es erfordert auch eine Koordinierung zwischen dem App-Code und den Angeboten, die wir später in der [!DNL Target] -Oberfläche definieren. Aufgrund dieser Koordinierung müssen Sie in einigen Personalisierungsfällen Ihre App möglicherweise im Appstore aktualisieren, um die Aktivität zu starten.

### Überprüfen der Echtzeitanforderung

Öffnen Sie den Android-Emulator und führen Sie alle Schritte aus, um eine Reise zu buchen: Startseite > Bussuchergebnisse > Sitzauswahl, Zahlungsoptionen (alle Zahlungsoptionen mit leeren Daten funktionieren).

Auf dem letzten Dankesbildschirm sehen Sie sich Logcat an, um die Antwort zu erhalten. Die Antwort sollte lauten: &quot;Standardinhalt wurde für &quot;wetravel_context_dest&quot;zurückgegeben:

![Fügen Sie auf dem Dankesbildschirm einen Echtzeitstandort hinzu](assets/thankyou_validation.jpg)

## Löschen von vorab abgerufenen Standorten aus dem Cache

Es kann Situationen geben, in denen vorab abgerufene Speicherorte während einer Sitzung gelöscht werden müssen. Wenn beispielsweise eine Buchung erfolgt, ist es sinnvoll, die zwischengespeicherten Standorte zu löschen, da der Benutzer jetzt &quot;interagiert&quot;ist und den Buchungsprozess versteht. Wenn sie während ihrer Sitzung eine weitere Reise buchen, benötigen sie nicht die ursprünglichen Orte auf der Startseite und auf dem Suchergebnisbildschirm, um ihre Buchung zu begleiten. Es wäre sinnvoller, die Speicherorte aus dem Cache zu löschen und neue Angebote vorab für eine ermäßigte zweite Buchung oder ein anderes relevantes Szenario abzurufen. Die Logik kann zum Startbildschirm und Suchergebnisbildschirm hinzugefügt werden, um neue Orte vorab abzurufen, wenn während der Sitzung eine Buchung stattgefunden hat.

In diesem Beispiel werden wir nur vorab abgerufene Orte für die Sitzung löschen, wenn eine Buchung stattfindet. Rufen Sie dazu die Funktion `Target.clearPrefetchCache()` auf. Legen Sie die Funktion innerhalb der Funktion `targetLoadRequest()` wie unten gezeigt fest:

```java
Target.clearPrefetchCache()
```

![Bereinigen von vorab abgerufenen Speicherorten aus dem Cache](assets/clearPrefetch.jpg)

Herzlichen Glückwunsch! Ihre App verfügt jetzt über das Framework für die Personalisierung. In der nächsten Lektion werden wir unsere Personalisierungsfunktionen erweitern, indem wir Parameter zu diesen Orten hinzufügen.

**[NEXT : &quot;Parameter hinzufügen&quot;>](add-parameters.md)**
