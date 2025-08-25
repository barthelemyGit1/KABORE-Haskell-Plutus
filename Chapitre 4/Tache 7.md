## HC4T7 - Tâche 7 : Ignorer des éléments dans une liste

Modifier firstAndThird pour ne retourner que le premier et le troisième élément d’une liste, en ignorant les autres.

---

### Code Haskell

```haskell
-- Fonction qui retourne le premier et le troisième élément d'une liste
firstAndThird :: [a] -> [a]
firstAndThird (x:_:z:_) = [x, z]   -- x = premier, _ = deuxième ignoré, z = troisième, _ = reste ignoré
firstAndThird _         = []        -- pour les listes de moins de 3 éléments

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ firstAndThird [1,2,3,4,5]     -- [1,3]
    print $ firstAndThird ["a","b","c"]   -- ["a","c"]
    print $ firstAndThird [10,20]         -- []
    print $ firstAndThird ([] :: [String]  ) -- []
```

---

### Explications

1. **Pattern matching sur les listes**

   ```haskell
   (x:_:z:_) 
   ```

   * `x` → premier élément.
   * `_` → deuxième élément, ignoré.
   * `z` → troisième élément.
   * `_` → le reste de la liste, ignoré.

2. **Cas générique pour les listes trop courtes**

   ```haskell
   firstAndThird _ = []
   ```

   * Si la liste contient moins de 3 éléments, on retourne une liste vide.

3. **Pureté**

   * La fonction `firstAndThird` est **pure** : le résultat dépend uniquement de l’entrée.

---

### Exemple de sortie

```
[1,3]
["a","c"]
[]
[]
```

---
