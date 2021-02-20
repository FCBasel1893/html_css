Flexbox vs Grid
===============

Flexbox = 1-dimensionale Layouts

Grid = 2-dimensionale Layouts

<br>

## Grid Line ##

Die Gitterlinien sind horizontal und vertikal und formen die Grundstruktur vom Gitter. (Grid)

Wir können Sie durch numerischen Zahlen referenzieren, beginnend mit 1.

<br>

## Grid Tracks ##

Eine Gitterspur ist der Raum zwischen zwei benachbarten Gitterlinien.
Sie sind die Zeilen und Spalten Ihres Rasters.

Wir können die Grid Tracks mit folgenden Selector trennen: (horizontal und vertikal)

`grid-row-gap` oder
`grid-column-gap`


<br>

## Grid Cell ##

Eine Gitterzelle ist der Raum zwischen 2 benachbarten Zeilengitterlinien *(rows)* und 2 benachbarten Spaltengitterlinien *(columns).*

Es ähnelt konzeptionell einer Tabellenzelle, da es die einzelne Einheit Ihres Rasters ist.

<br>

## Grid Areas ##

Ein Gitterbereich besteht aus einer oder mehreren Gitterzellen *(grid cells)* und ist auf jeder Seite des Gitterbereichs durch 4 Gitterlinien begrenzt.
Sie können auf einen Rasterbereich verweisen, indem Sie seine Begrenzungsgitterlinien oder seinen Namen verwenden, wie in der Eigenschaft `grid-template-areas` definiert.

<br>
<br>

Aktivieren des Gitters (Grid)
=============================

## Display: Grid ##

Ähnlich wie bei der Verwendung von Flexbox muss das CSS-Grid-Modul aktiviert sein. 
In der Regel erfolgt dies durch Einstellen 
`Display: grid;` auf dem übergeordneten Container.

<br>

Andere mögliche Werte sind:

`display: inline-grid` und `display: subgrid`

<br>

## Behältereigenschaften (Container) ##

Selectoren:   `grid-template-columns` und `grid-template-rows`

Diese beiden Eigenschaften geben die Größe der Rasterspuren *(grid tracks)* und Liniennamen an. Der Eigenschaftswert wird als durch Leerzeichen getrennte Liste ausgedrückt, die als Titelliste bezeichnet wird.

<br>

*Mögliche Werte:*
`Keine` | `track-list` | `auto-track-list`

...aber was ist eine `track-list`

Eine Liste von Werten, die die Größe jeder Gitterspur und die Namen der Gitterlinien angeben (optional).

**Beispiel**

.grid {

  dislay: grid;

  grid-template-columns: 150px 400px 200px;
}

<br>

## Containereigenschaften ##

**Beispiel**

.container {

  grid-template-columns: 40px 50px auto 50px 40px; 
  
  *(horizontal - 4 Spalten, auto ist variabel)*
  
  grid-template-rows: 25% 100px auto; 
  
  *(vertikal - 3 Spalten)*
}

<br>





Container
=========



.container {
  display: grid;
  grid-template-columns: 100px 100px 200px 200px; (Spalten horizontal)
  grid-template-rows: 100px 100px 200px 200px; (Spalten vertikal)

  grid-template-colums: 200px repeat(4, 100px) --> 1 Spalte 200px + 4 Spalten jeweils 100px breit
  grid-template-colums: 5fr repeat(4, 1fr); (9 Spalten -- 5/9 + 4x 1 Spalte) -->fr steht für Bruchteil

  grid-templates-areas: "header header header header"
                        "line 1 line 1 line 1 line 1"
                        "line 2 line 2 line 2 line 2"
                        "line 3 line 3 line 3 line 3"
                        "line 4 line 4 line 4 line 4"


grid-templates

Anordnung im Feld (1 Raster)
justify-items: center/end/start;
align-items: center/end/start;


Abstände zwischen den Spalten                        
grid-gap: 10px; (horizontal + vertikal)
grid-column-gap: 10px; (nur horizontal)
grid-row-gap: 10px; (nur vertikal)


.item {
  grid-row-start: 1; (Zeile 1 Start)
  grid-row-end: 3; (Zeile 3 End)
  grid-column-start: 1; (Spalte 1 Start)
  grid-column-end: 4; (Spalte 4 End)
  background-color: blue;
}





items
=====

align-self: start/end/center; (innerhalb der Spalte horizontal eingemittet)
justify-self: start/end/center (innerhalb der Zeile vertikal eingemittet)