### Übung 5.02: Suchen von Filmen nach Genre und Paginieren von Ergebnissen
```
var findMoviesByGenre = function(genre, pageNumber, pageSize){
      let toSkip = 0;
      if(pageNumber < 2){
          toSkip = 0;
      } else{
          toSkip = (pageNumber -1) * pageSize;
      }
      let movies = db.movies.find(
          {"genres" : genre}, 
          {"_id" : 0, "title" :1})
      .sort({"imdb.rating" : -1})
      .skip(toSkip)
      .limit(pageSize)
      .toArray()
      print("************* Page : " + pageNumber)
      for(let i=0; i<movies.length; i++){
          print(movies[i].title)
      }
}
```
