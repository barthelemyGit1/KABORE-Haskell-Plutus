## HC12T7 : Calculer l’aire d’un cercle

Créer une fonction calculateCircleArea qui calcule l’aire d’un cercle à partir de son rayon. La fonction main doit démontrer son utilisation.

---

### Code haskell
```haskell
-- Définition de la fonction pour calculer l'aire
calculateCircleArea :: Floating a => a -> a
calculateCircleArea r = pi * r * r

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez le rayon du cercle :"
    input <- getLine
    let radius = read input :: Double
    let area = calculateCircleArea radius
    putStrLn $ "L'aire du cercle est : " ++ show area
```

---

### Explications :

1. **Fonction `calculateCircleArea`** :

   * Prend un rayon `r` et retourne `π * r^2`.
   * `Floating a => a -> a` permet de travailler avec `Float` ou `Double`.

2. **Lecture du rayon** :

   ```haskell
   input <- getLine
   let radius = read input :: Double
   ```

3. **Calcul et affichage de l’aire** :

   ```haskell
   let area = calculateCircleArea radius
   putStrLn $ "L'aire du cercle est : " ++ show area
   ```
