## HC5T9 : Fonction d’ordre supérieur pour transformer une liste

Écrire une fonction d’ordre supérieur transformList qui applique deux fois une fonction donnée à chaque élément d’une liste.

---

### Code Haskell

```haskell
-- Applique une fonction deux fois à chaque élément d'une liste
transformList :: (a -> a) -> [a] -> [a]
transformList f xs = map (f . f) xs

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ transformList (+1) [1,2,3]     -- [3,4,5]  ((1+1)+1+1?)
    print $ transformList (*2) [1,2,3]     -- [4,8,12]
    print $ transformList (\x -> x^2) [1,2,3] -- [1,16,81]
```

---

### Explications

1. **Fonction d’ordre supérieur**

   * `transformList` prend **une fonction `f`** et **une liste `xs`**.
   * Elle retourne une nouvelle liste où chaque élément a été transformé par `f . f`.

2. **Composition de fonctions**

   ```haskell
   f . f
   ```

   * Équivaut à `\x -> f (f x)`
   * On applique donc `f` **deux fois** à chaque élément.

3. **`map`**

   * Applique une fonction à **chaque élément** d’une liste.
   * Ici, `map (f . f) xs` transforme tous les éléments.

---

### Exemple de sortie

```
[3,4,5]
[4,8,12]
[1,16,81]
```
