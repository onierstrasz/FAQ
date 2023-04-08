# PetitParser FAQ

## Q Where is the main documentation?

https://kursjan.github.io/petitparser2/

## Q What are all the combinators?

```
p1 , p2 	(sequence)
p1 / p2		(ordered choice)
p star		(zero or more)
p plus		(one or more p)
p optional	(optional)
p negate	(consume any but p)
p and		(match but don't consume)
p not		(don't match and don't consume)
p end		(match end of input after p)
```
But there are also some other for island grammars ...
