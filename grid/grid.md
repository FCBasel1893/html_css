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