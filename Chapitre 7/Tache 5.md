## HC7T5 : Fonction utilisant la contrainte Num

Écrire une fonction squareArea qui calcule l’aire d’un carré à partir de la longueur d’un côté. La fonction doit fonctionner avec tout type numérique.

Parfait 💡 Ici, on veut une fonction **générique** qui calcule l’aire d’un carré à partir de la longueur de son côté.

En Haskell, on utilise la contrainte **`Num a`** pour dire que la fonction fonctionne avec tout type numérique (`Int`, `Float`, `Double`, etc.).

---

### Code Haskell

```haskell
-- Fonction générique pour l'aire d'un carré
squareArea :: Num a => a -> a
squareArea side = side * side

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ squareArea (5 :: Int)      -- 25
    print $ squareArea (4.5 :: Float)  -- 20.25
    print $ squareArea (3.2 :: Double) -- 10.24
```

---

### Explications

1. **Signature**

   ```haskell
   squareArea :: Num a => a -> a
   ```

   * `Num a =>` : `a` doit être un type numérique (contrainte).
   * `a -> a` : prend un nombre, retourne un nombre du même type.

2. **Implémentation**

   ```haskell
   squareArea side = side * side
   ```

   * Aire d’un carré = côté × côté.
   * Comme `*` appartient à la classe `Num`, cela marche avec `Int`, `Float`, `Double`, etc.

3. **Tests**

   * Avec des entiers (`Int`).
   * Avec des flottants (`Float`, `Double`).

---

### Exemple de sortie

```
25
20.25
10.24
```
