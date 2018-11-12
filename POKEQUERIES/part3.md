# Part 3: Joins and Groups

##What is each pokemon's primary type?
SELECT poke.name, t.name
FROM pokemon.pokemons poke
       JOIN pokemon.types t
         ON poke.primary_type = t.id;

##What is Rufflet's secondary type?
SELECT poke.name, t.name
FROM pokemon.pokemons poke
JOIN pokemon.types t
On poke.secondary_type = t.id
WHERE poke.name = "Rufflet";

##What are the names of the pokemon that belong to the trainer with trainerID 303?
SELECT poke.name
FROM pokemon.pokemons poke
JOIN pokemon.pokemon_trainer poketrainer
ON poke.id = poketrainer.pokemon_id
Where poketrainer.trainerID = 303;

##How many pokemon have a secondary type `Poison`?
SELECT COUNT(poke.secondary_type)
FROM pokemon.pokemons poke
JOIN pokemon.types poketypes
ON poke.secondary_type = poketypes.id
WHERE poketypes.name = "Poison";

##What are all the primary types and how many pokemon have that type?
SELECT poketypes.name, COUNT(poke.name)
FROM pokemon.types poketypes
JOIN pokemon.pokemons poke
ON poke.primary_type = poketypes.id
GROUP BY poketypes.name;


##How many pokemon at level 100 does each trainer with at least one level 100 pokemon have?
##(Hint: your query should not display a trainer
SELECT  COUNT(pokelevel) AS "Level 100 Pokemon"
from pokemon.pokemon_trainer
where pokelevel = 100
group by  trainerID;

##How many pokemon only belong to one trainer and no other?
SELECT count(1) as pokemon_has_one_trainer
FROM (select poke.name, count(poketrainer.trainerID)
from pokemon.pokemons poke left join pokemon.pokemon_trainer poketrainer
on poke.id = poketrainer.pokemon_id
group by poke.name
having count(poketrainer.trainerID) = 1) a;

