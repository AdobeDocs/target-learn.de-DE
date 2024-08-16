---
title: Implementieren von at.js 2.0 in Einzelseiten-Apps (SPA)
description: Adobe Target at.js 2.0 bietet umfassende Funktionen, mit denen Ihr Unternehmen mithilfe von Client-seitigen Technologien der neuesten Generation Personalisierungen ausführen kann. Führen Sie diese Schritte aus, um at.js 2.0 in einer Einzelseiten-App (SPA) zu implementieren.
role: Developer
level: Intermediate
topic: SPA, Architecture, Development
feature: Implementation
doc-type: technical video
kt: null
author: Daniel Wright
exl-id: 955f0571-5791-4dbb-9931-e6d5c8bb42a7
source-git-commit: 80208b3ecbc0d627d2afe72f882e91c9800d2726
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%
---

# Implementieren von Adobe Target at.js 2.0 in eine Einzelseiten-App (SPA)

Adobe Target `at.js` 2.0 bietet umfassende Funktionen, mit denen Ihr Unternehmen mithilfe von Client-seitigen Technologien der neuesten Generation Personalisierungen ausführen kann. Diese Version konzentriert sich auf die Aktualisierung von `at.js`, um harmonische Interaktionen mit Einzelseitenanwendungen (SPA) zu ermöglichen.

>[!VIDEO](https://video.tv.adobe.com/v/26248?quality=12)

## Implementieren von at.js 2.0 in einer SPA

* Implementieren Sie `at.js` 2.0 im &lt;head> Ihrer Einzelseiten-App.
* Implementieren Sie die Funktion &quot;`adobe.target.triggerView()`&quot;, wenn sich die Ansicht in Ihrer SPA ändert. Hierfür können verschiedene Verfahren eingesetzt werden, z. B. das Überwachen von URL-Hash-Änderungen, das Überwachen von benutzerdefinierten Ereignissen, die von Ihrer SPA ausgelöst werden, oder das Einbetten des `triggerView()`-Codes direkt in Ihre Anwendung. Sie sollten die Option auswählen, die am besten für Ihre spezifische Einzelseitenanwendung geeignet ist.
* Der Ansichtsname ist der erste Parameter der Funktion `triggerView()` . Verwenden Sie einfache, klare und eindeutige Namen, damit sie im Visual Experience Composer von Target leicht ausgewählt werden können.
* Sie können Trigger-Ansichten in kleinen Ansichtsänderungen sowie in nicht SPA Kontexten wie der halben Navigation nach unten auf einer unendlichen Scrollseite anzeigen.
* `at.js` 2.0 und `triggerView()` können über eine Tag-Management-Lösung wie Adobe Experience Platform Launch implementiert werden.

## Einschränkungen von at.js 2.0

Beachten Sie vor dem Upgrade die folgenden Einschränkungen von `at.js` 2.0:

* Domänenübergreifendes Tracking wird in `at.js` 2.0 nicht unterstützt
* Die URL-Parameter mboxOverride.browserIp und mboxSession werden in `at.js` 2.0 nicht unterstützt
* Die alten Funktionen mboxCreate, mboxDefine, mboxUpdate werden in `at.js` 2.0 nicht mehr unterstützt. Standardinhalt wird angezeigt und es werden keine Netzwerkanfragen gestellt.

## Im Video verwendeter Bibliotheksfußzeilencode

Der unten stehende Code wurde während des Videos zum Abschnitt &quot;Bibliotheksfußzeile&quot;der `at.js` -Bibliothek hinzugefügt. Sie wird ausgelöst, wenn die App zuerst geladen wird und dann bei jeder Hash-Änderung in der App. Es verwendet eine bereinigte Version des Hash als Ansichtsnamen und &quot;home&quot;, wenn der Hash leer ist. Beachten Sie, dass der Code zur Identifizierung des SPA nach dem Text &quot;react/&quot;in der URL sucht, der höchstwahrscheinlich auf Ihrer Site aktualisiert werden muss. Beachten Sie auch, dass es für Ihre SPA angemessener sein kann, `triggerView()` benutzerspezifische Ereignisse auszulösen oder den Code direkt in Ihre App einzubetten.

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
* [Verwenden von Adobe Target Visual Experience Composer für Einzelseiten-Apps (SPA VEC)](../experiences/use-the-visual-experience-composer-for-single-page-applications.md)

