**SASS / SCSS**
===============

## **Was ist Sass?** ##
Sass (Syntactically Awesome Stylesheets) ist eine Stylesheet-Sprache, die als Präprozessor die Erzeugung von Cascading Style Sheets erleichtert. Sie wurde ursprünglich beeinflusst von der Auszeichnungssprache YAML.

<br>

## **SCSS (Sass CSS) Syntax** ##

`$meineFarbe: #3BBFCE` (Variable wird definiert)



.navigation {


  border-color: `$meineFarbe`

  color: darken (`$meineFarbe`, 9%)
}



 ### Warum? ###
 1. Strukturierte Schreibweise mittels Verschachtelung möglich

2. Variablen (zur Kompilierungszeit)

<br>

## **Basics Variablen** ##

Sass Variablen können Strings, Zahlen, Farben usw. beinhalten. Konsequent eingesetzt, machen sie dein Projekt maximal flexibel in Bezug auf Farben, Abstände und Schriftarten.

<br>

**Beispiel**

`$primary-color: #333;`

body {

  background-color: `$primary-color;`

}

<br>

## **Basics Verschachtelung** ##

<br>

### **Pure CSS** ###



.column-left { 

  width: 100%;
}

<br>

.column-left .title {

  color: red;
  font-size: 18px;
}

<br>

.column-left .sub-title {

  color: red;
  font-size: 14px;
}

<br>

.column-left .text {

  color: red;
  font-size: 12px;
}

<br>

### **Sass** ##

.column-left {

  width: 100%;


<br>

  .title {

    color: red;
    font-size: 18px;
  }

<br>

  .sub-title {

    color: red;
    font-size: 14px;
  }

<br>

  .text {

     color: red;
    font-size: 12px;
  }

}

<br>

## **Verschachtelung von Properties** ##

<br>

### **Pure CSS** ##


.column-left { 

  font-size: 10px;

  font-family: Verdana, sans-serif;

  font-weight: 300;

}

<br>

### **Sass** ###


.column-left { 

  font: {

    size: 10px;
    family: Verdana, sans-serif;
    weight: 300;
  }

  /* andere styles */
}


<br>

## **Basics: &-Operator** ##

In einer Verschachtelung hat der & (Ampersand)-Operator eine spezielle Bedeutung.Er beinhaltet den Selektor des umschliessenden Blocks. Dies ist insbesondere zur sauberen Strukturierung und für die Umsetzung von Namenskonventionen wie z.B. BEM nützlich. 

<br>

**Beispiel**

.navigation {

  &-item {

    width: 20px;
    height: 20px;
  }

}

<br>

## **Basics: Mathematische Operatoren** ##

Sass kann auch für euch rechnen. Dies ist nützlich, wenn ihr z.B. eine Breite im als Variable definiert habt. Beachtet allerdings, dass diese Berechnung beim Kompilieren durch den Präprozessor stattfindet und nicht in eurem Browser.

<br>

**Beispiel**

`$container-width:` 400px;

<br>

.navigation-item {

  width: `$container-width` / 2;  --> geteilt durch 2

  height: 20px;

}

Mögliche Operatoren: 

addieren / suptrahieren / dividieren / multiplizieren / modulo

<br>

## **Basics Farb-Operatoren** ##

Sass kann basierend auf einer Farbe weitere Farbwerte berechnen.

<br>

Verfügbar sind:
* darken() / lighten()              `dunkel/hell`
* saturate() / desaturate()          `sättigung`
* adjust-hue()                      `Farbton einstellen`
* rgba()                            `rot grün blau + transparenz`

<br>

## **Basics: Partials** ##

Mit Sass kannst du deine Styles in kleinere Dateien aufteilen, die dann z.B. jeweils die Styles für eine einzelne Komponente enthalten.
Zusätzlich könntest du ein Partial für die Farben erstellen.

Die Dateinamen der Partials beginnen jeweils mit 

`_ (Underscore).`

<br>

**Beispiele**

_colors.scss

_navigation.scss

_footer.scss


<br>


## **Basics: Imports** ##

Partials bindest du mittels @import in deine Hauptdatei ein. Der Inhalt der zu importierenden Dateien wird dann durch den Präprozessor in dein kompiliertes CSS geladen.

<br>

**Beispiel**

`@import “components/colors”;`

`@import “components/header”;`

<br>

!!! Nicht zu verwechseln mit CSS @import `<url>;`

<br>

Bei CSS wird ein zusätzlicher Request zum Server geschickt und die per URL definierte CSS-Datei angefordert (=> langsam)

<br>

Beachte, dass du beim Schreiben des Import-Statements den ?`Unterstrich _` welchen du im Namen des Partials angegeben hast, sowie die Endung `“.scss”` weglassen kannst.

<br>

**Falsch:**
@import “components/_colors.scss”;

**Richtig:**
@import “components/colors”;


<br>

## **Basics Loops** ##

Möchtest du eine Serie von CSS-Regeln erstellen, so kannst du auf den `@for Loop von SCSS` zurückgreifen.

<br>

@for $i from 1 through 10 {

  .todo:nth-child(#{$i}) {

    background-color: darken(#ff0000, $i * 5);
    color: lighten(#ff0000, $i * 25);
  }

}

<br>

## **Installation Node-Sass** ##

Führe folgendes Kommando in deinem Terminal aus: 

`npm install -g node-sass`
Damit installierst du den Sass-Präprozessor. Damit dieser nun SCSS in CSS übersetzt, musst du jeweils im *Terminal* in deinem *Übungsverzeichnis* folgendes Kommando ausführen: 

`node-sass main.scss main.css`

Damit du effizient entwickeln kannst, gibt es auch einen `“watcher”`, der die Änderungen in der SCSS-Datei feststellt und jeweils den Präprozessor in Gang setzt. Das obige kommando muss dann wie folgt ergänzt werden:

`node-sass --watch main.scss main.css`
