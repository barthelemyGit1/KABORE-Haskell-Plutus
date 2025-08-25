## HC6T5 : Inverser une liste (récursif)

Implémente une fonction qui inverse une liste en utilisant la récursion.

---

### Code Haskell

```haskell
-- Fonction récursive pour inverser une liste
reverseList :: [a] -> [a]
reverseList []     = []                 -- Cas de base : liste vide
reverseList (x:xs) = reverseList xs ++ [x] -- Cas récursif

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ reverseList [1,2,3,4,5]      -- [5,4,3,2,1]
    print $ reverseList ["a","b","c"]    -- ["c","b","a"]
    print $ reverseList  ([] :: [String])  -- []
```

---

### Explications

1. **Cas de base**

   ```haskell
   reverseList [] = []
   ```

   * Une **liste vide** inversée est toujours vide.

2. **Cas récursif**

   ```haskell
   reverseList (x:xs) = reverseList xs ++ [x]
   ```

   * `x:xs` : `x` est le premier élément, `xs` est le reste de la liste.
   * On inverse récursivement `xs`, puis on ajoute `x` à la **fin**.

3. **Pureté**

   * La fonction est **pure** : dépend uniquement de l’entrée.

---

### Exemple de sortie

```
[5,4,3,2,1]
["c","b","a"]
[]
```
