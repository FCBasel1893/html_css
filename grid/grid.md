**Flexbox vs Grid**
===================

**Flexbox** = 1-dimensionale Layouts

**Grid** = 2-dimensionale Layouts

<br>

## **Grid Line (container)** ##

Die Gitterlinien sind horizontal und vertikal und formen die Grundstruktur vom Gitter. *(Grid)*

Wir können Sie durch numerischen Zahlen referenzieren, beginnend mit 1.

<br>

## **Grid Tracks (container)** ##

Eine Gitterspur ist der Raum zwischen zwei benachbarten Gitterlinien.
Sie sind die Zeilen und Spalten Ihres Rasters.

Wir können die Grid Tracks mit folgenden Selector trennen: *(horizontal und vertikal)*

`grid-row-gap` oder
`grid-column-gap`


<br>

## **Grid Cell (container)** ##

Eine Gitterzelle ist der Raum zwischen 2 benachbarten Zeilengitterlinien *(rows)* und 2 benachbarten Spaltengitterlinien *(columns).*

Es ähnelt konzeptionell einer Tabellenzelle, da es die einzelne Einheit Ihres Rasters ist.

<br>

## **Grid Areas (container)** ##

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

## **Behältereigenschaften (Container)** ##

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

## **Containereigenschaften** ##

**Beispiel**

.container {

  grid-template-columns: 40px 50px auto 50px 40px; 
  
  *(horizontal - 4 Spalten, auto ist variabel)*
  
  grid-template-rows: 25% 100px auto; 
  
  *(vertikal - 3 Spalten)*
}

<br>

## **Grid-Template-Areas (container)** ##


Diese Eigenschaft definiert benannte Rasterbereiche *(grid areas)* und bietet eine Visualisierung der Rasterstruktur, wodurch das Verständnis des zugrunde liegenden Codes erleichtert werden kann.

**Mögliche Werte:**
`Keine` | `<string>+`

... aber was ist mit `<string>+`

Jede separate Zeichenfolge erstellt eine Zeile, während jedes Wort in der Zeichenfolge *(string)* eine Spalte erstellt.
Alle *Strings* müssen die gleiche Anzahl von Wörtern haben, andernfalls ist die Deklaration ungültig. 
Die Verwendung einer Folge von einem oder mehreren "." Stellt ein Nullzellen-Token dar, bei dem es sich um einen unbenannten Bereich im Raster handelt.

<br>

**Beispiel**

.container {

  grid-template-areas: 
  
    "logo stats"

    "score stats"

    board board"

    "... controls";
}

<br>

.container {

  grid-template-columns: 50px 50px 50px 50px; **oder**

  grid-template-columns: repeat(4, 50px)

  grid-templates-rows: auto;

  grid-templates-areas: `"header header header header"` 
 
  (4 Spalten header - horizontal (column))


  `"main main . sidebar"` 
  
  (2 Spalten main / 1 Spalte leer (.) 1 Spalte sidebar)

  `"footer footer footer footer"`

  (4 Spalten footer)

}

<br>

Die verkürzte Schreibweise für `grid-template-columns` + `grid-template-rows` + `grid-template-areas` ist:

      `grid-template: none;`

<br>

## **grid-column-gap und grid-row-gap (container)** ##


Diese Eigenschaften geben den Raum zwischen Rasterspalten 
*(column)* bzw. Rasterzeilen *(rows)* an.

Mögliche Werte: `<length>` oder `<percentage>`

<br>

## **grid-gap (container)** ##

 `grid-gap` ist eine abgekürzte Schreibweise für `grid-row-gap` und `grid-column-gap`

<br>

 ## **justify-items** ##

 Wir können den Inhalt innerhalb von Rasterelementen in der Inline-Dimension oder entlang der Zeilenachse 
 *(row-axis  <--->)* ausrichten, indem wir die Eigenschaft `justify-items` auf den Rastercontainer anwenden.

 Mögliche Werte:
 `center | start | end | strech`

 <br>

 ## **align-items (container)** ##

 Wir können die Ausrichtung für den Inhalt innerhalb von Rasterelementen in der Blockdimension oder entlang der Spaltenachse *(column-axis - horizontal)* festlegen, indem wir die Eigenschaft `align-items` auf den Rastercontainer anwenden.

Mögliche Werte:
 `center | start | end | strech`

 <br>
 <br>

 **item properties**
 ===================

 ## **grid-column-start, grid-column-end and grid-row-start, grid-row-end** ##

 Diese vier Eigenschaften definieren die Größe eines Rasterelements und wo es im Raster platziert werden soll.
 Zusammen geben sie an, welche Gitterlinien die Kanten des Gitterbereichs eines Gitterelements bilden.

<br>

 **Beispiel**

 .item-a {
   + grid-column-start: 2; *(2. Linie horizontal)*
   + grid-column-end: 5; *(5. Linie horizontal)*
   + grid-row-start: row1-start; *(1. Linie vertikal)*
   + grid-row-end: 3; *(3. Linie vertikal)*
 }

 <br>

## **grid-column and grid-row** ##

 Dies ist eine Abkürzung, die die Start- und Endlinie für die jeweiligen Dimensionen in derselben Deklaration festlegt.

<br>

 **Format:**

 grid-column: 
 
 `<start-line> / <end-line> / <start-line> / span <value>`;

 grid-row: 
 
 `<start-line> / <end-line> / <start-line> / span <value>`;

<br>

## **grid-area** ##

Dies ist eine Abkürzung, mit der die Gitterlinien festgelegt werden, die jede der 4 Kanten des Gitterbereichs in einer einzelnen Deklaration definieren. Alternativ können Sie hier auch den Alias ​​der Spalte verwenden.

<br>

**Die Reihenfolge dieser Kurzform lautet:**

`row start / column-start / row-end / column-end`

<br>

## **justify-self** ##

Wir können den Inhalt innerhalb eines einzelnen Rasterelement `grid items` in der Inline-Dimension oder entlang der Zeilenachse (*row-axis) bestimmen, 
indem wir die Eigenschaft `justify-self` auf das Rasterelement `grid item itself` selbst anwenden.


Mögliche Werte:
 `center | start | end | strech`

 <br>

## **align-self** ##

Wir können die Ausrichtung für den Inhalt innerhalb einzelner Rasterelemente `grid items` in der Blockdimension oder entlang der Spaltenachse `column-axis` festlegen, indem wir die Eigenschaft `align-self` auf das Rasterelement `grid item itself` selbst anwenden.


Mögliche Werte:
 `center | start | end | strech`


<br>
<br>

**Container (Beispiele)**
=========================



.container {

  display: grid;

  grid-template-columns: 100px 100px 200px 200px; (Spalten horizontal)
  grid-template-rows: 100px 100px 200px 200px; (Spalten vertikal)

  grid-template-colums: 200px repeat(4, 100px) --> 1 Spalte 200px + 4 Spalten jeweils 100px breit
  grid-template-colums: 5fr repeat(4, 1fr); (9 Spalten -- 5/9 + 4x 1 Spalte) -->fr steht für Bruchteil

  grid-templates-areas: 
                        
                        "header header header header"
                        "line 1 line 1 line 1 line 1"
                        "line 2 line 2 line 2 line 2"
                        "line 3 line 3 line 3 line 3"
                        "line 4 line 4 line 4 line 4"

<br>

# **grid-templates** #

<br>

**Anordnung im Feld (1 Raster)**

justify-items: center/end/start;
align-items: center/end/start;


**Abstände zwischen den Spalten** 

grid-gap: 10px; (horizontal + vertikal)
grid-column-gap: 10px; (nur horizontal)
grid-row-gap: 10px; (nur vertikal)

<br>

.item {

  grid-row-start: 1; *(Zeile 1 Start)*

  grid-row-end: 3; *(Zeile 3 End)*

  grid-column-start: 1; *(Spalte 1 Start)*

  grid-column-end: 4; *(Spalte 4 End)*

  background-color: blue;
}

<br>

items
=====

align-self: 

`start/end/center`; (innerhalb der Spalte horizontal eingemittet)

justify-self: 
`start/end/center` (innerhalb der Zeile vertikal eingemittet)