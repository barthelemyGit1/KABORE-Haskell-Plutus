## HC6T3 : Somme des éléments avec foldr

Implémente une fonction qui calcule la somme des éléments d’une liste en utilisant foldr.

---

### Code Haskell

```haskell
-- Somme des éléments avec foldr
sumList :: [Int] -> Int
sumList = foldr (+) 0

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ sumList [1,2,3,4,5]    -- 15
    print $ sumList []             -- 0
    print $ sumList [10,20,30]     -- 60
```

---

### Explications

1. **`foldr`**

   ```haskell
   foldr (+) 0 [1,2,3,4,5]
   ```

   * `foldr` prend **une fonction binaire**, un **accumulateur initial**, et une **liste**.
   * Ici :

     * Fonction : `(+)`
     * Accumulateur initial : `0`
     * Liste : `[1,2,3,4,5]`
   * Évaluation : `1 + (2 + (3 + (4 + (5 + 0)))) = 15`

2. **Pureté**

   * La fonction `sumList` est **pure**, dépend uniquement de sa liste d’entrée.

3. **Avantage de `foldr`**

   * Permet de réduire une liste avec n’importe quelle fonction binaire, pas seulement `+`.

---

### Exemple de sortie

```
15
0
60
```
