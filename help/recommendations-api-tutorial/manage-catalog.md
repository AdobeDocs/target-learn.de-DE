---
title: Verwalten Ihres Recommendations-Katalogs mithilfe von APIs
description: Dieser Teil des Tutorials führt Entwickler durch die Schritte, die zur Verwendung von Adobe Target-APIs zum Erstellen, Aktualisieren, Speichern, Abrufen und Löschen von Entitäten in Ihrem Recommendations-Katalog erforderlich sind.
role: Developer
level: Intermediate
topic: Personalization, Administration, Integrations, Development
feature: APIs/SDKs, Recommendations, Administration & Configuration
doc-type: tutorial
kt: 3815
author: Judy Kim
exl-id: 8060b69b-e8e5-4fe7-895f-742410d8ed45
source-git-commit: 342e02562b5296871638c1120114214df6115809
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---

# Verwalten Ihres [!DNL Recommendations]-Katalogs mithilfe von APIs

An dieser Stelle haben Sie gelernt, wie Sie mithilfe des JWT-Authentifizierungsflusses ein Zugriffstoken generieren, um die Adobe Target Admin-APIs mit Adobe I/O zu verwenden.

Sie können die [Recommendations-APIs](https://developers.adobetarget.com/api/recommendations/) verwenden, um Elemente in Ihrem Empfehlungskatalog hinzuzufügen, zu aktualisieren oder zu löschen. Wie bei den anderen Adobe Target Admin-APIs erfordern die [!DNL Recommendations]-APIs eine Authentifizierung.

>[!TIP]
>
>Senden Sie **[!UICONTROL IMS: JWT Generate + Auth über User Token]** anfordern, wann immer Sie Ihr Zugriffstoken zur Authentifizierung aktualisieren müssen, da es nach 24 Stunden abläuft. Anweisungen finden Sie unter [Adobe API-Authentifizierung konfigurieren](../apis/configure-io-target-integration.md) .

![JWT3ff](assets/configure-io-target-jwt3ff.png)

>[!NOTE]
>
>Bevor Sie fortfahren, rufen Sie die [Recommendations Postman-Sammlung](https://developers.adobetarget.com/api/recommendations/#section/Postman) ab.

## Erstellen und Aktualisieren von Elementen mit der API &quot;Entitäten speichern&quot;

Um Ihre [!DNL Recommendations]-Produktdatenbank mit der API anstatt mit einem CSV-Produkt-Feed oder [!DNL Target]-Anforderungen zu füllen, die auf Produktseiten ausgelöst werden, verwenden Sie die [Entitäten-API speichern](https://developers.adobetarget.com/api/recommendations/#operation/saveEntities). Diese Anfrage fügt ein Element in einer einzelnen [!DNL Target]-Umgebung hinzu oder aktualisiert es. Die Syntax lautet:

```
POST https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities
```

So können beispielsweise &quot;Save Entities&quot;verwendet werden, um Artikel zu aktualisieren, wenn bestimmte Schwellenwerte erreicht werden (z. B. Werte für Inventar oder Preis), um diese Elemente zu kennzeichnen und zu verhindern, dass sie empfohlen werden.

1. Navigieren Sie zu **[!DNL Target]> [!UICONTROL Setup] > [!UICONTROL Hosts] > [!UICONTROL Umgebungen]** , um die [!DNL Target] Umgebungs-ID abzurufen, zu der Sie ein Element hinzufügen oder aktualisieren möchten.

   ![SaveEntities1](assets/SaveEntities01.png)

2. Überprüfen Sie `TENANT_ID` und `API_KEY`, ob Sie auf die zuvor eingerichteten Postman-Umgebungsvariablen verweisen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![SaveEntities3](assets/SaveEntities03.png)

3. Geben Sie Ihren JSON-Code als **raw**-Code im **Body** ein. Vergessen Sie nicht, Ihre Umgebungs-ID mithilfe der Variablen `environment` anzugeben. (Im folgenden Beispiel ist die Umgebungs-ID 6781.)

   ![SaveEntities4.png](assets/SaveEntities04.png)

   >!![NOTE]
   Nachfolgend finden Sie ein Beispiel-JSON, das entity.id kit2001 mit den zugehörigen Entitätswerten für ein Toaster Oven-Produkt in die Umgebung 6781 hinzufügt.

   ```
      {
      "entities": [{
              "name": "Toaster Oven",
              "id": "kit2001",
              "environment": 6781,
              "categories": [
                  "housewares:appliances"
              ],
              "attributes": {
                  "inventory": 77,
                  "margin": 23,
                  "message": "crashing helicopter",
                  "pageUrl": "www.foobar.foo.com/helicopter.html",
                  "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                  "value": 19.2
              }
          }]
      }
   ```

4. Klicken Sie auf **Senden**. Sie sollten die folgende Antwort erhalten.

   ![SaveEntities5.png](assets/SaveEntities05.png)

Das JSON-Objekt kann skaliert werden, um mehrere Produkte zu senden. Diese JSON gibt beispielsweise zwei Entitäten an.

```
    {
        "entities": [{
                "name": "Toaster Oven",
                "id": "kit2001",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 89,
                    "margin": 11,
                    "message": "Toaster Oven",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 102.5
                }
            },
            {
                "name": "Blender",
                "id": "kit2002",
                "environment": 6781,
                "categories": [
                    "housewares:appliances"
                ],
                "attributes": {
                    "inventory": 36,
                    "margin": 5,
                    "message": "Blender",
                    "pageUrl": "www.foobar.foo.com/helicopter.html",
                    "thumbnailUrl": "www.foobar.foo.com/helicopter.jpg",
                    "value": 54.5
                }
            }
        ]
    }
```

1. Jetzt bist du dran! Verwenden Sie die API **Save Entities** , um Ihrem Katalog die folgenden Elemente hinzuzufügen. Verwenden Sie die obige JSON-Beispieldatei als Ausgangspunkt. (Sie müssen die JSON-Datei um weitere Entitäten erweitern.)

   ![SaveEntities6.png](assets/SaveEntities06.png)

Ups, sieht so aus, als ob die letzten beiden Dinge nicht gehören. Untersuchen wir sie mithilfe der API **Get Entity** und löschen Sie sie bei Bedarf mithilfe der API **Delete Entities**.

## Abrufen von Elementdetails mit der Get Entity API

Um die Details eines vorhandenen Elements abzurufen, verwenden Sie die [Entitäts-API abrufen](https://developers.adobetarget.com/api/recommendations/#operation/getEntity). Die Syntax lautet:

```
GET https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities/[entity.id]
```

Entitätsdetails können jeweils nur für eine Entität abgerufen werden. Sie können &quot;Entität abrufen&quot;verwenden, um zu bestätigen, dass im Katalog Aktualisierungen wie erwartet vorgenommen wurden, oder um anderweitig den Inhalt des Katalogs zu überprüfen.

1. Geben Sie in der API-Anfrage die Entitäts-ID mithilfe der Variablen `entityId` an. Im folgenden Beispiel werden Details für die Entität zurückgegeben, deren entityId=kit2004 lautet.

   ![GetEntity1](assets/GetEntity1.png)

2. Überprüfen Sie `TENANT_ID` und `API_KEY`, ob Sie auf die zuvor eingerichteten Postman-Umgebungsvariablen verweisen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![GetEntity2](assets/GetEntity2.png)

3. Senden Sie die Anfrage.

   ![GetEntity3](assets/GetEntity3.png)
Wenn Sie einen Fehler erhalten, der besagt, dass die Entität nicht gefunden wurde (wie im Beispiel oben gezeigt), überprüfen Sie, ob Sie die Anforderung an die richtige  [!DNL Target] Umgebung senden.

   >[!NOTE]
   Wenn keine Umgebung explizit angegeben ist, versucht &quot;Get Entity&quot;, die Entität nur aus Ihrer [Standardumgebung](https://experienceleague.adobe.com/docs/target/using/administer/hosts.html?lang=en) abzurufen. Wenn Sie von einer anderen Umgebung als der Standardumgebung abrufen möchten, müssen Sie die Umgebungs-ID angeben.

4. Fügen Sie bei Bedarf den Parameter `environmentId` hinzu und senden Sie die Anfrage erneut.

   ![GetEntity4](assets/GetEntity4.png)

5. Senden Sie eine weitere **Get Entity**-Anfrage, diesmal zur Überprüfung der Entität, deren entityId=kit2005 lautet.

   ![GetEntity5](assets/GetEntity5.png)

Angenommen, Sie entscheiden, dass diese Entitäten aus Ihrem Katalog entfernt werden müssen. Verwenden wir die API **Entitäten löschen**.

## Löschen von Elementen mit der API &quot;Entitäten löschen&quot;

Um Elemente aus Ihrem Katalog zu entfernen, verwenden Sie die [API zum Löschen von Entitäten](https://developers.adobetarget.com/api/recommendations/#operation/deleteEntities). Die Syntax lautet:

```
DELETE https://mc.adobe.io/{{TENANT_ID}}/target/recs/entities?ids=[comma-delimited-entity-ids]&environment=[environmentId]
```

>[!WARNING]
Diese API löscht Entitäten, die von Ihnen angegebenen IDs referenziert werden.
Wenn keine Entitäts-IDs bereitgestellt werden, werden alle Entitäten in der angegebenen Umgebung gelöscht. Wenn keine Umgebungs-ID angegeben wird, werden Entitäten aus allen Umgebungen gelöscht. Seien Sie vorsichtig!

1. Navigieren Sie zu **[!DNL Target]> [!UICONTROL Setup] > [!UICONTROL Hosts] > [!UICONTROL Umgebungen]** , um die [!DNL Target] Umgebungs-ID abzurufen, aus der Sie Elemente löschen möchten.

   ![DeleteEntities1](assets/SaveEntities01.png)

2. Geben Sie in der API-Anfrage mithilfe der Syntax `&ids=[comma-delimited-entity-ids]` (Abfrageparameter) die Entitäts-IDs der Entitäten an, die Sie löschen möchten. Trennen Sie beim Löschen mehrerer Entitäten die IDs durch Kommas.

   ![DeleteEntities2](assets/DeleteEntities2.png)

3. Geben Sie die Umgebungs-ID mithilfe der Syntax `&environment=[environmentId]` an. Andernfalls werden Entitäten in allen Umgebungen gelöscht.

   ![DeleteEntities3](assets/DeleteEntities3.png)

4. Überprüfen Sie `TENANT_ID` und `API_KEY`, ob Sie auf die zuvor eingerichteten Postman-Umgebungsvariablen verweisen. Verwenden Sie das folgende Bild zum Vergleich. Ändern Sie bei Bedarf die Kopfzeilen und den Pfad in Ihrer API-Anfrage so, dass sie mit denen in der Abbildung unten übereinstimmen.

   ![DeleteEntities4](assets/DeleteEntities4.png)

5. Senden Sie die Anfrage.

   ![DeleteEntities5](assets/DeleteEntities5.png)

6. Überprüfen Sie Ihre Ergebnisse mit **Get Entity**, was jetzt darauf hinweisen sollte, dass die gelöschten Entitäten nicht gefunden werden können.

   ![DeleteEntities6](assets/DeleteEntities6.png)

   ![DeleteEntities6](assets/DeleteEntities7.png)

Herzlichen Glückwunsch! Sie können jetzt die [!DNL Recommendations]-APIs verwenden, um Details zu den Entitäten in Ihrem Katalog zu erstellen, zu aktualisieren, zu löschen und abzurufen. Im nächsten Abschnitt erfahren Sie, wie Sie benutzerdefinierte Kriterien verwalten.

[Weiter mit &quot;Benutzerdefinierte Kriterien verwalten&quot;>](manage-custom-criteria.md)
