# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


REponse au questions 
a) Total des objets Album :
Album.count
  Album Count (0.1ms)  SELECT COUNT(*) FROM "albums"
 => 343 

 b) Auteur de la chanson "White Room" :
 Track.find_by(title: "White Room").artist
  Track Load (0.2ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."title" = ? LIMIT ?  [["title", "White Room"], ["LIMIT", 1]]
 => "Britney Spears" 

 c) Chanson durant exactement 188133 milliseconds :
  Track.find_by(duration: 188133).title
  Track Load (0.2ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."duration" = ? LIMIT ?  [["duration", 188133], ["LIMIT", 1]]
 => "Perfect" 

 d) Groupe ayant sorti l'album "Use Your Illusion II" :
 Album.find_by(title: "Use Your Illusion II").artist
  Album Load (0.1ms)  SELECT "albums".* FROM "albums" WHERE "albums"."title" = ? LIMIT ?  [["title", "Use Your Illusion II"], ["LIMIT", 1]]
 => "Guns N Roses" 

 Niveau Moyen
a) Nombre d'albums contenant "Great" dans le titre :
Album.where("title LIKE ?", "%Great%").count
  Album Count (0.2ms)  SELECT COUNT(*) FROM "albums" WHERE (title LIKE '%Great%')
 => 13 

b) Supprimer tous les albums dont le nom contient "music" :
Album.where("title LIKE ?", "%music%").destroy_all
  Album Load (0.2ms)  SELECT "albums".* FROM "albums" WHERE (title LIKE '%music%')
 => [] 

 c) Nombre d'albums écrits par AC/DC :
 Album.where(artist: "AC/DC").count
  Album Count (0.1ms)  SELECT COUNT(*) FROM "albums" WHERE "albums"."artist" = ?  [["artist", "AC/DC"]]
 => 2

d) Nombre de chansons durant exactement 158589 milliseconds :
 Track.where(duration: 158589).count
  Track Count (0.6ms)  SELECT COUNT(*) FROM "tracks" WHERE "tracks"."duration" = ?  [["duration", 158589]]
 => 0 

 Niveau Difficile
a) Afficher tous les titres de AC/DC :
Track.where(artist: "AC/DC").each { |track| puts track.title }
  Track Load (0.2ms)  SELECT "tracks".* FROM "tracks" WHERE "tracks"."artist" = ?  [["artist", "AC/DC"]]
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie

b) Afficher tous les titres de l'album "Let There Be Rock" :
For Those About To Rock (We Salute You)
Put The Finger On You
Lets Get It Up
Inject The Venom
Snowballed
Evil Walks
C.O.D.
Breaking The Rules
Night Of The Long Knives
Spellbound
Go Down
Dog Eat Dog
Let There Be Rock
Bad Boy Boogie
Problem Child
Overdose
Hell Aint A Bad Place To Be
Whole Lotta Rosie

c) Prix total et durée totale de l'album "Let There Be Rock" :
Prix total: 7.92, Durée totale: 2453259 milliseconds

d) Coût de l'intégralité de la discographie de "Deep Purple" :
total_cost = Track.where(artist: "Deep Purple").sum(:price)
3.2.2 :019 > puts "Coût total de la discographie de Deep Purple: #{total_cost}"
  Track Sum (0.2ms)  SELECT SUM("tracks"."price") FROM "tracks" WHERE "tracks"."artist" = ?  [["artist", "Deep Purple"]]
Coût total de la discographie de Deep Purple: 90.09
 => nil 

 