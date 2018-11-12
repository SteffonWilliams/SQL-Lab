### Part 4: Final Report
##Directions: Write a query that returns the following columns:
SELECT a.name as Pokemon_Name	, b.trainername as Trainer_Name	, c.PokeLevel, d.name as Primary_Type	, e.name as Secondary_Type
from pokemon.pokemon_trainer c     join pokemon.pokemons a
         on a.id = c.pokemon_id    join pokemon.trainers b
         on b.trainerID = c.trainerID join pokemon.types d
         on a.primary_type = d.id     join pokemon.types e
         on a.secondary_type = e.id
order by PokeLevel desc
#Sort the data by finding out which trainer has the strongest pokemon so that this will act as a ranking of strongest to weakest trainer.

