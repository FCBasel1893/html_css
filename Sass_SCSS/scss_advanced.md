**SCSS Advanced**
==================

## Mixins ##

Ein Mixin erlaubt es euch, repetitive Teile eures CSS-Codes zu abstrahieren. So können diese nachher wiederverwendet werden.

<br>

Hätte man beispielsweise im CSS mehrfach folgenden CSS-Code:

`a:link { color: white; }`

`a:visited { color: blue; }`

`a:hover { color: green; }`

`a:active { color: red; }`

<br>

## Mixins: Definition ##

Könnte mit folgendem Mixin abstrahiert werden:

```
@mixin linx ($link, $visit, $hover, $active) {

  a {
    color: $link;
    
    &:visited {
      color: $visit;
    }
    &:hover {
      color: $hover;   
    }
    &:active {
      color: $active;
    }
  }
}
```

<br>

## Mixins: Aufruf ##

`@include variable (white, blue, green, red);`

<br>

Willst du die Argumente in beliebiger Reihenfolge übergeben, kannst du die Keyword-Arguments Schreibweise verwenden.

`@include variable ($visit: blue, $hover: red, $active: green, $link: white);`

<br>

## Mixins: Default-Werte

Du kannst auch Default-Werte für Parameter definieren,
welche optional sind:

```
@mixin headline($size, $color: red) {
  color: $color;
  font-size: $size;
}
```

<br>

## Mixins: @content ##

Mithilfe der **@content-Direktive** kannst du einen Style-Block in die Direktive übergeben, welcher im Mixin nicht definiert ist.

```
@mixin cont {
  background-color: black;
  color: white;
  @content;
}
```
```
div {
  @include cont {
    font-size: 12px;
    font-style: italic;
  }
}
```

<br>

## if/else Verwendung ##

In Sass kannst du auch If/Else-Statements verwenden, um den Inhalt einer Variable oder eines Arguments zu prüfen.
Zum Beispiel ob “left” oder “right” übergeben wurde.

```
if/else
@mixin test($direction) {
  @if $direction == ‘left’ {
    text-align: left;
  } @else {
    text-align: right;
  }
}

.foo {
  @include test(left);
}
```
```
Ausgabe:

.foo {
  text-align: left;
}
```


<br>

## Extends: Verwendung ##

Wenn du möchtest, dass Sass beliebige Styles von einem existierenden Selektor zu einem Weiteren übernimmt, so verwendest du @extend.

```
Verwendung:
.foo {
  font-size: 12px;
  color: red;
}

.bar {
  @extend .foo;
}
````

```
Ausgabe:

.foo, .bar {
  font-size: 12px;
  color: red;
}
```
<br>

## Extends: Abgrenzung zu Mixins ##

Im ersten Moment erscheinen Mixins und Extends das selbe. Klarheit schafft ein Codeschnipsel zum Mixin:

```
Mixin:
@mixin stuff {
  font-size: 12px;
  color: red;
}

.foo {
  @include stuff;
}

.bar {
  @include stuff;
}
```

```
Ausgabe:
.foo {
  font-size: 12px;
  color: red;
}

.bar {
  font-size: 12px;
  color: red;
}
```

<br>

## Placeholders: Verwendung ##

Verwendest du @extend mit normalen Selektoren, so werden diese ganz normal im CSS abgebildet. Möchtest du eine CSS-Klasse extenden, die dann nicht im CSS auftauchen, kannst du einen Placeholder Selektor verwenden.

```
Placeholder:
%stuff {
  font-size: 12px;
  color: red;
}

.foo {
  @extend %stuff;
}
```

```
Ausgabe:
.foo {
  font-size: 12px;
  color: red;
}
```





