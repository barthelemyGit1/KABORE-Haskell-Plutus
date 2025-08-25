## HC6T4 : Produit des éléments avec foldl

Implémente une fonction qui calcule le produit des éléments d’une liste en utilisant foldl.

---

### Code Haskell

```haskell
-- Produit des éléments avec foldl
productList :: [Int] -> Int
productList = foldl (*) 1

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ productList [1,2,3,4,5]    -- 120
    print $ productList []             -- 1
    print $ productList [2,3,4]        -- 24
```

---

### Explications

1. **`foldl`**

   ```haskell
   foldl (*) 1 [1,2,3,4,5]
   ```

   * `foldl` prend **une fonction binaire**, un **accumulateur initial**, et une **liste**.
   * Ici :

     * Fonction : `(*)`
     * Accumulateur initial : `1`
     * Liste : `[1,2,3,4,5]`
   * Évaluation : `((((1*1)*2)*3)*4)*5 = 120`

2. **Cas de liste vide**

   * La multiplication sur une liste vide retourne `1` (élément neutre de `*`).

3. **Pureté**

   * La fonction `productList` est **pure**, dépend uniquement de sa liste d’entrée.

---

### Exemple de sortie

```
120
1
24
```

---

Si tu veux, je peux te montrer **la version équivalente avec `foldr`** et expliquer la différence subtile entre `foldr` et `foldl`. Veux‑tu que je fasse ça ?
