## HC7T3 : Fonction avec contraintes multiples

Écrire une fonction compareValues qui prend deux arguments de type a et retourne le plus grand.

Assurez-vous que a est une instance de Eq et Ord.

---

### Code Haskell

```haskell
-- compareValues : retourne la plus grande des deux valeurs
compareValues :: (Eq a, Ord a) => a -> a -> a
compareValues x y
    | x >= y    = x
    | otherwise = y

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ compareValues 10 20       -- 20
    print $ compareValues 3 3         -- 3 (les deux sont égaux)
    print $ compareValues 'a' 'z'     -- 'z'
    print $ compareValues "apple" "banana" -- "banana"
```

---

### Explications

1. **Signature avec contraintes multiples**

   ```haskell
   (Eq a, Ord a) => a -> a -> a
   ```

   * `Eq a` : permet d’utiliser `==` ou `>=`.
   * `Ord a` : permet de comparer avec `<`, `>`, `>=`, `<=`.
   * La fonction prend **deux valeurs du même type** et retourne une valeur de ce type.

2. **Définition**

   ```haskell
   | x >= y    = x
   | otherwise = y
   ```

   * Si `x` est plus grand ou égal à `y`, on retourne `x`.
   * Sinon, on retourne `y`.

3. **Exemples**

   * Avec des `Int`, des `Char`, ou même des `String` (puisque `String` est une instance de `Eq` et `Ord`).

---

### Exemple de sortie

```
20
3
'z'
"banana"
```

---

Haskell a déjà une fonction intégrée `max`, donc on aurait pu écrire :

```haskell
compareValues = max
```
