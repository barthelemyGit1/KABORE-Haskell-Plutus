## HC6T7 : Taille d’une liste

Implémente une fonction qui prend une liste et retourne sa longueur.

---

### Code Haskell

```haskell
-- Fonction récursive pour calculer la longueur d'une liste
listLength :: [a] -> Int
listLength []     = 0                      -- Cas de base : liste vide → longueur 0
listLength (_:xs) = 1 + listLength xs      -- Cas récursif : compter 1 + longueur du reste

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ listLength [1,2,3,4,5]    -- 5
    print $ listLength []             -- 0
    print $ listLength ["a","b","c"]  -- 3
```

---

### Explications

1. **Cas de base**

   ```haskell
   listLength [] = 0
   ```

   * Une liste vide a une longueur de `0`.

2. **Cas récursif**

   ```haskell
   listLength (_:xs) = 1 + listLength xs
   ```

   * On ignore (`_`) le premier élément, et on compte **1** + la longueur du reste de la liste `xs`.

3. **Type**

   * `[a] -> Int` : fonctionne pour **toute liste** d’éléments de n’importe quel type.

---

### Exemple de sortie

```
5
0
3
```
