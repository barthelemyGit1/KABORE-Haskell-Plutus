## HC8T3 : Types algébriques et fonctions

Définir un type Shape avec les constructeurs Circle Float et Rectangle Float Float.

Créer une fonction area :: Shape -> Float qui calcule l’aire de la forme.

Calculer l’aire d’un cercle de rayon 5 et d’un rectangle de côtés 10 et 5.

---

```haskell
-- Définition du type Shape
data Shape
  = Circle Float            -- constructeur pour un cercle avec rayon
  | Rectangle Float Float   -- constructeur pour un rectangle avec longueur et largeur
  deriving (Show)

-- Fonction qui calcule l'aire
area :: Shape -> Float
area (Circle r) = pi * r * r
area (Rectangle l w) = l * w

-- Exemples d'utilisation
main :: IO ()
main = do
  let c = Circle 5
      r = Rectangle 10 5
  putStrLn ("Aire du cercle (rayon 5) : " ++ show (area c))
  putStrLn ("Aire du rectangle (10x5) : " ++ show (area r))
```

### Explications :

* `Circle Float` représente un cercle de rayon `Float`.
* `Rectangle Float Float` représente un rectangle avec deux côtés.
* `area` fait un **pattern matching** sur la forme pour appliquer la bonne formule.

  * Cercle : $π × r^2$
  * Rectangle : $longueur × largeur$

👉 Résultat attendu :

```
Aire du cercle (rayon 5) : 78.53982
Aire du rectangle (10x5) : 50.0
```
