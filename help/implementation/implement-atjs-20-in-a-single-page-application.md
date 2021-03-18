---
title: Implementieren von "at.js 2.0"in einer Einzelseitenanwendung (SPA)
description: Adobe Targets at.js 2.0 bietet umfassende Funktionssätze, die Ihr Unternehmen in die Lage versetzen, Personalisierungen auf clientseitigen Technologien der nächsten Generation auszuführen. Führen Sie folgende Schritte aus, um at.js 2.0 in eine Einzelseitenanwendung (SPA) zu implementieren.
role: Entwickler
level: Zwischenschaltung
topic: SPA, Architektur, Entwicklung
feature: Implementierung
doc-type: technical video
kt: null
thumbnail: null
author: Daniel Wright
translation-type: tm+mt
source-git-commit: b89732fcca0be8bffc6e580e4ae0e62df3c3655d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---


# &quot;at.js 2.0&quot;in Adobe Target in einer Einzelseitenanwendung implementieren (SPA)

Adobe Targets `at.js` 2.0 bietet umfassende Funktionssätze, die Ihr Unternehmen in die Lage versetzen, Personalisierungen auf clientseitigen Technologien der nächsten Generation auszuführen. Diese Version konzentriert sich auf die Aktualisierung von `at.js`, um harmonische Interaktionen mit Einzelseitenanwendungen (SPA) zu haben.

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Implementieren von &quot;at.js 2.0&quot;in einer SPA

* Implementieren Sie `at.js` 2.0 im &lt;head> der Einzelseitenanwendung.
* Implementieren Sie die Funktion `adobe.target.triggerView()`, wenn sich die Ansicht in Ihrer SPA ändert. Dazu können verschiedene Methoden eingesetzt werden, z. B. das Listening auf Änderungen am URL-Hash, das Listening auf benutzerdefinierte Ereignis, die von Ihrem SPA ausgelöst werden, oder das Einbetten des `triggerView()`-Codes direkt in Ihre Anwendung. Sie sollten die Option wählen, die für Ihre spezifische Einzelseitenanwendung am besten geeignet ist.
* Der Name der Ansicht ist der erste Parameter der Funktion `triggerView()`. Verwenden Sie einfache, klare und eindeutige Namen, um sie im Visual Experience Composer der Zielgruppe auszuwählen.
* Sie können Ansichten in kleiner Ansicht sowie in nicht SPA Kontexten, wie z. B. in der Mitte einer unendlichen Bildlaufseite, Trigger werden.
* `at.js` 2.0 und  `triggerView()` kann über eine Tag-Management-Lösung wie Adobe Experience Platform Launch implementiert werden.

## at.js 2.0-Einschränkungen

Beachten Sie vor der Aktualisierung die folgenden Einschränkungen von `at.js` 2.0:

* Die domänenübergreifende Verfolgung wird in `at.js` 2.0 nicht unterstützt
* Die URL-Parameter mboxOverride.browserIp und mboxSession werden in `at.js` 2.0 nicht unterstützt
* Die alten Funktionen mboxCreate, mboxDefine, mboxUpdate werden in `at.js` 2.0 nicht mehr unterstützt. Standardinhalt wird angezeigt und es werden keine Netzwerkanforderungen gesendet.

## Im Video verwendeter Bibliotheksfußzeilencode

Der unten stehende Code wurde während des Videos zum Abschnitt &quot;Bibliotheksfußzeile&quot;der Bibliothek `at.js` hinzugefügt. Es wird ausgelöst, wenn die App zuerst geladen wird und dann bei jeder Hash-Änderung in der App. Es verwendet eine bereinigte Version des Hashs als Ansicht und &quot;Home&quot;, wenn der Hash leer ist. Beachten Sie, dass der Code zur Identifizierung des SPA nach dem Text &quot;response/&quot;in der URL sucht, der höchstwahrscheinlich auf Ihrer Site aktualisiert werden muss. Denken Sie auch daran, dass es für Ihre SPA angemessener sein könnte, `triggerView()` von benutzerdefinierten Ereignissen auszulösen oder den Code direkt in Ihre App einzubetten.

```javascript
function sanitizeViewName(viewName) {
  if (viewName.startsWith('#')) {
    viewName = viewName.substr(1);
  }
  if (viewName.startsWith('/')) {
    viewName = viewName.substr(1);
  }
  return viewName;
}
function triggerView(viewName) {
  viewName = sanitizeViewName(viewName) || 'home';
  // Validate if the Target Libraries are available on your website
  if (typeof adobe != 'undefined' && adobe.target && typeof adobe.target.triggerView === 'function') {
    adobe.target.triggerView(viewName);
    console.log('AT: View triggered on page load: '+viewName)
  }
}
//fire triggerView when the SPA loads and when the hash changes in the SPA
if(window.location.pathname.indexOf('react/') >-1){
    triggerView(location.hash);
}
window.onhashchange = function() {
    if(window.location.pathname.indexOf('react/') >-1){
        triggerView(location.hash);
    }
}
```

## Zusätzliche Ressourcen

* [Funktionsweise von at.js 2.0 (Architekturdiagramme)](understanding-how-atjs-20-works.md)
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseitenanwendungen (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)
* [Aktualisierung der Dokumentation von &quot;at.js 1.x&quot;auf &quot;at.js 2.0&quot;](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/upgrading-from-atjs-1x-to-atjs-20.html)