## HC7T6 : Utiliser Integral et Floating

Définir une fonction circleCircumference qui prend un rayon et retourne la circonférence. Elle doit fonctionner avec des types Integral et Floating.

---

Pour calculer la **circonférence d’un cercle**, on utilise la formule :

$$
C = 2 \pi r
$$

En Haskell, `pi` est de type `Floating`, donc pour que la fonction fonctionne avec des types **`Integral`** (comme `Int` ou `Integer`) et `Floating` (comme `Float`, `Double`), il faut convertir les entiers en flottants avec `fromIntegral`.

---

### Code Haskell

```haskell
-- Circonférence d'un cercle
circleCircumference :: (Integral a, Floating b) => a -> b
circleCircumference radius = 2 * pi * fromIntegral radius

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ circleCircumference (5 :: Int)       -- 31.41592653589793
    print $ circleCircumference (10 :: Integer)  -- 62.83185307179586
    print $ circleCircumference (7 :: Int)       -- 43.982297150257104
```

---

### Explications

1. **Signature**

   ```haskell
   (Integral a, Floating b) => a -> b
   ```

   * `a` : type entier (`Int`, `Integer`).
   * `b` : type flottant (`Float`, `Double`).
   * `fromIntegral` convertit `a` en `b`.

2. **Conversion**

   ```haskell
   fromIntegral radius
   ```

   * Permet de multiplier un entier par `pi` qui est flottant.

3. **Formule**

   ```haskell
   2 * pi * fromIntegral radius
   ```

   * Applique directement la formule de la circonférence.

4. **Tests**

   * Fonctionne avec `Int` et `Integer`.
   * Retourne un résultat de type flottant (`Double` par défaut).

---

### Exemple de sortie

```
31.41592653589793
62.83185307179586
43.982297150257104
```
