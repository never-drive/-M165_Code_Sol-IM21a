### Übung 6b.01: Aktualisieren der IMDb- und Tomatometer-Bewertung
Kunden der Filmdatenbank schätzen es immer noch, einige der zeitlosen klassischen Filme anzusehen,
zu bewerten oder ihre Rezensionen zu posten. Ihre Firma hat entschieden, Bewertungsaktualisierungen 
für alle Filme unabhängig von ihrem Veröffentlichungsdatum zu integrieren. Als Proof of Concept haben 
sie "The Godfather" ausgewählt und Sie beauftragt, diesen Film mit den neuesten IMDb- und Tomatometer-Bewertungen 
zu aktualisieren. 

Dies sind die neuesten IMDb- und Tomatometer-Bewertungen des Films:
* IMDb
  - Bewertung: 9.2
  - Stimmen: 1'565'120
* Tomatometer
  - Bewertung: 4.76 
  - Anzahl der Bewertungen: 733'777
  - Meter: 98


### Aufgaben
1. Verwenden Sie mflix-Datenbank
```
use mflix
```
2. Analysieren Sie den genannten Eintrag und deren Bewertungen
```
db.movies.find(
  {"title" : "The Godfather"}
)
//besser
db.movies.find(
  {"title" : "The Godfather"},
  {"imdb":1, title:1, "tomatoes.viewer" : 1, "_id" : 0}
)
```
3. Aktualisieren Sie den Eintrag mit den vorgegebenen IMDb- und Tomatometer-Bewertungen.
Dabei sollen nur die IMDB-, Tomaten-Bewertung, keine Document-ID und das aktualisierte Dokument beim Update
ausgegeben werden.
```
db.movies.findOneAndUpdate(
  {"title" : "The Godfather"},
  {
    $set: {
      "imdb.rating" : 9.2,
      "imdb.votes" : 1565120,
      "tomatoes.viewer.rating": 4.76,
      "tomatoes.viewer.numReviews": 733777,
      "tomatoes.viewer.meter": 98
    }
  },
  {
    "projection" : {"imdb" : 1, "tomatoes.viewer" : 1, "_id" : 0},
    "returnNewDocument" : true
  }
)
```